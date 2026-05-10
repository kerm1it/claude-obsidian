# NotebookLM Queue Sub-Processor

Use this sub-processor when a source is too complex for direct agent extraction, but NotebookLM may be able to index it and expose usable text, guides, or cited answers.

NotebookLM is treated as an **asynchronous external indexing service**, not a synchronous extractor. Large files, videos, audio, and rich documents can take minutes or fail after a long preparation period, so this processor uses a queue file and bounded waits.

Purpose: submit complex sources to NotebookLM, track their progress in `.raw/.notebooklm-queue.json`, extract ready sources into `.raw/notebooklm/`, and then continue through the normal `wiki-ingest` Single Source Ingest flow.

---

## When To Use

Run this when direct reading or ordinary URL/file ingestion is unreliable:

- Large or image-heavy PDFs
- Audio or video files
- YouTube URLs
- Slide decks or mixed-media documents
- EPUB / Word / other document formats that local tools cannot parse cleanly
- Web sources where normal extraction fails but NotebookLM can ingest the URL

Do not use this for simple Markdown, text, CSV, clean HTML, or files the agent can already read completely.

---

## Queue File

Queue path:

```text
.raw/.notebooklm-queue.json
```

Create it on first use:

```json
{
  "version": 1,
  "updated_at": "YYYY-MM-DDTHH:MM:SSZ",
  "items": []
}
```

This queue is agent-maintained metadata, similar to `.raw/.manifest.json`. It may be updated by `wiki-ingest`; other source files under `.raw/` remain immutable.

---

## Queue Item Schema

Each item should be flat JSON:

```json
{
  "id": "notebooklm-20260510-demo",
  "original_source": "/absolute/path/or/url",
  "source_hash": "sha256-or-md5-when-local-file",
  "source_kind": "file|url|youtube|audio|video|pdf|other",
  "created_at": "YYYY-MM-DDTHH:MM:SSZ",
  "updated_at": "YYYY-MM-DDTHH:MM:SSZ",
  "status": "submitted",
  "notebook_id": "",
  "source_id": "",
  "notebook_title": "",
  "source_title": "",
  "attempts": 1,
  "last_error": "",
  "last_checked_at": "",
  "target_raw_path": ".raw/notebooklm/slug-YYYY-MM-DD.md",
  "extraction_method": "",
  "retention": "retained",
  "notes": ""
}
```

Use a stable `id` derived from the source path/URL plus date. For local files, record a hash so repeated submissions can be detected.

---

## Statuses

- `submitted`: Notebook and source were created; NotebookLM has not finished indexing.
- `processing`: Source is still preparing/processing.
- `extracted`: A Markdown intermediate source exists in `.raw/notebooklm/`; by default it should proceed to wiki ingest.
- `ingested`: The `.raw/notebooklm/` source has completed Single Source Ingest.
- `failed`: NotebookLM returned an explicit error or extraction failed.
- `needs-user-decision`: The agent needs the user to choose retry, keep, delete, fallback, pause, or abandon.
- `paused`: User explicitly asked not to ingest this source yet.
- `abandoned`: User chose not to continue processing, but the queue record is retained.
- `deleted`: NotebookLM notebook/source cleanup was confirmed and completed.

Default path:

```text
submitted -> processing -> extracted -> ingested
```

Exception path:

```text
submitted/processing -> failed -> needs-user-decision
```

Do not add an `auto_ingest` boolean. The default is to ingest after extraction unless the item is `paused` or `needs-user-decision`.

---

## Ingest Preflight

At the start of every `wiki-ingest` run:

1. If `.raw/.notebooklm-queue.json` exists, read it before processing the new source.
2. Check `submitted` and `processing` items with `notebooklm source list --notebook [id] --json`.
3. If any item becomes extractable, extract it into `.raw/notebooklm/` and set status `extracted`.
4. If there are `extracted` items, ask the user whether to process the queue before the new source.
5. If the user says yes, ingest extracted queue items first, then continue with the requested source.
6. If there are `failed` or `needs-user-decision` items, summarize them and ask what to do. Do not delete anything automatically.

If the user explicitly asks to process the NotebookLM queue, run this preflight even when there is no new source.

---

## Submit Flow

When a new complex source arrives:

1. Run readiness checks:

   ```bash
   notebooklm status
   notebooklm list --json
   ```

   If auth is missing or expired, stop and ask the user to run `notebooklm login`.

2. Create a dedicated notebook:

   ```bash
   notebooklm create "Ingest: [short title]" --json
   ```

   Parse `.notebook.id`.

3. Add the source:

   ```bash
   notebooklm source add "[path-or-url]" --notebook "[notebook_id]" --json
   ```

   Parse `.source.id` when returned. If the CLI blocks but `source list` shows a source was created, record that source id.

4. Immediately write or update the queue item with status `submitted`.

5. Wait synchronously for at most 5 minutes:

   ```bash
   notebooklm source wait "[source_id]" -n "[notebook_id]" --timeout 300
   ```

6. If ready, continue to **Extraction Flow**.

7. If timeout, update status to `processing`, record `last_checked_at`, and stop the NotebookLM sub-processor for now. Tell the user the item is queued and will be checked before future ingests.

---

## Queue Check Flow

For each `submitted` or `processing` item:

1. Query source state:

   ```bash
   notebooklm source list --notebook "[notebook_id]" --json
   ```

2. If the source status is ready, run **Extraction Flow**.
3. If the source status is still preparing/processing, keep or set status `processing`.
4. If the source status is error, set status `failed`, record the status and CLI output, then set `needs-user-decision`.
5. If the notebook or source cannot be found, set `needs-user-decision` and record the lookup error.

Do not wait more than a few seconds during preflight unless the user explicitly asks to wait.

---

## Extraction Flow

The extraction flow has two main paths:

1. **Fulltext path**: preserve NotebookLM's indexed source text when it is available and sufficiently complete.
2. **Report path**: ask NotebookLM to generate a structured Markdown report, wait for the artifact, and download it.

Use guide/chat only as fallback or diagnostics, not as the primary output path.

### 1. Fulltext Path

Run:

```bash
notebooklm source fulltext "[source_id]" --notebook "[notebook_id]" --json
```

Parse the returned JSON:

- Use `.content` as the main extracted text.
- Use `.title` as the extracted source title when present.
- Use `.char_count` to judge whether the extraction is substantial.

If `.content` is non-empty and substantial, write `target_raw_path` under `.raw/notebooklm/` using:

```yaml
extraction_method: fulltext
confidence: high
```

Then put `.content` under `## Extracted Content`.

If `.content` is missing, very short, or clearly incomplete for the source type, use the Report Path.

### 2. Report Path

Use NotebookLM's report artifact generation for complex formats, especially video, audio, slide decks, image-heavy PDFs, and sources where fulltext is unavailable.

Start a custom report task:

```bash
notebooklm generate report \
  "Extract this source into structured Markdown for wiki ingestion. Include key claims, entities, concepts, dates, unresolved questions, and notable quotes. Preserve source-specific details. Do not over-summarize." \
  --format custom \
  --source "[source_id]" \
  --notebook "[notebook_id]" \
  --json
```

`--json` here is for the CLI control plane: it returns task metadata such as `task_id` and `status`. It does **not** mean the generated report content is JSON.

Parse `.task_id`, then wait for the report artifact:

```bash
notebooklm artifact wait "[task_id]" -n "[notebook_id]" --timeout 900
```

Download the completed report as Markdown:

```bash
notebooklm download report "[target_raw_path]" -a "[task_id]" -n "[notebook_id]"
```

After download, prepend or merge the standard frontmatter and `## Extraction Notes` from the **Intermediate Source Contract**. Use:

```yaml
extraction_method: report-custom
confidence: medium
```

Set `confidence: low` if the report is too summary-like, lacks source-specific details, or omits important modalities.

### 3. Fallback / Diagnostics

If both Fulltext Path and Report Path fail, try:

```bash
notebooklm source guide "[source_id]" --notebook "[notebook_id]"
```

and:

```bash
notebooklm ask "Extract the source into structured Markdown with key claims, entities, concepts, dates, unresolved questions, and notable quotes. Include citation markers where available." --notebook "[notebook_id]" -s "[source_id]" --json
```

For `ask --json`, use `.answer` as extracted text and append `.references` under `## NotebookLM References`.

Only set status `extracted` from fallback output if the result passes the quality gate. Otherwise set `needs-user-decision`.

Set status to `extracted` after the intermediate Markdown file passes the quality gate. Then, by default, proceed to Single Source Ingest unless the user has paused the item.

---

## Intermediate Source Contract

Path:

```text
.raw/notebooklm/[slug]-[YYYY-MM-DD].md
```

Frontmatter:

```markdown
---
source_type: notebooklm-extract
original_source: "[path-or-url]"
fetched: [YYYY-MM-DD]
notebooklm_notebook_id: "[id]"
notebooklm_source_id: "[id]"
notebooklm_queue_id: "[queue-item-id]"
notebooklm_retention: retained
extraction_method: "[fulltext|report-custom|source-guide|cited-qa|mixed]"
confidence: [high|medium|low]
---
```

Body:

```markdown
# NotebookLM Extract: [title]

## Extraction Notes

- Original source: [path-or-url]
- NotebookLM notebook: [title] ([id])
- NotebookLM source: [title] ([id])
- Method: [method]
- Limits: [what may be missing]

## Extracted Content

[fulltext content, downloaded report content, source guide, cited Q&A synthesis, or mixed extraction]
```

---

## Quality Gate

Before setting `extracted`:

- Confirm the `.raw/notebooklm/` file exists.
- Confirm it contains enough content to support entity/concept extraction.
- Mark `confidence: low` if the output is mostly a NotebookLM summary rather than fulltext.
- Record missing modalities, such as images, tables, speaker labels, formulas, or slide notes.
- Record any extraction errors in `## Extraction Notes`.

---

## Failure Policy

Failures are not cleanup events.

When processing fails:

1. Set status to `failed`.
2. Record `last_error`, NotebookLM status/status_id, command output summary, and timestamp.
3. Set status to `needs-user-decision`.
4. Present choices to the user:
   - retry with a new notebook/source
   - keep and check later
   - delete NotebookLM notebook/source
   - fallback to another extractor, such as local transcription/OCR
   - pause
   - abandon

Retry rules:

- Do not automatically retry large files, audio, or video.
- For small documents, one automatic retry is allowed only if the failure looks transient.
- Every retry increments `attempts` and should create fresh NotebookLM IDs unless the previous source is clearly still usable.

---

## Retention And Cleanup

Default: retain NotebookLM notebooks and sources after extraction and ingest.

Reasons:

- They allow later citation checks and follow-up questions.
- They make `.raw/notebooklm/` outputs auditable.
- They help diagnose weak extractions.

Deletion rules:

- Ask before deleting notebooks or sources.
- Delete only the notebook/source referenced by the queue item.
- After confirmed cleanup, set `retention: deleted` and status `deleted` only if no further ingest work remains.
- If cleanup fails, keep the queue record and write the failure into `last_error`.

Use:

```bash
notebooklm source delete "[source_id]" --notebook "[notebook_id]"
notebooklm delete -n "[notebook_id]" --yes
```

---

## Automation Policy

Recurring automation may process the queue by default:

- Check `submitted` and `processing` items.
- Extract ready sources into `.raw/notebooklm/`.
- Continue to Single Source Ingest for `extracted` items unless they are `paused` or `needs-user-decision`.
- Update `.raw/.notebooklm-queue.json`, `.raw/.manifest.json`, `wiki/log.md`, `wiki/hot.md`, and related wiki pages as normal ingest would.

Automation must not:

- Delete NotebookLM notebooks or sources without user confirmation.
- Resolve contradictions silently.
- Retry large failed media automatically.
- Ignore `needs-user-decision` or `paused` statuses.

Every automated ingest must leave a normal `wiki/log.md` entry and update the queue item to `ingested` or `needs-user-decision`.

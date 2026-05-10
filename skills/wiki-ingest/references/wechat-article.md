# WeChat Article Sub-Processor

Use this sub-processor when ingesting a WeChat public-account article whose URL host is `mp.weixin.qq.com`, especially links shaped like `https://mp.weixin.qq.com/s/<id>`.

Purpose: turn WeChat's script-heavy article HTML into a clean immutable source file under `.raw/articles/`, then return to the main `wiki-ingest` Single Source Ingest flow.

---

## When To Use

Run this before ordinary URL ingestion when:

- URL host is `mp.weixin.qq.com`
- The user provides a WeChat public-account article link
- Generic WebFetch returns noisy HTML, script output, or no usable prose

If this sub-processor cannot extract a non-empty article body, fall back to ordinary URL ingestion or ask the user for an exported copy.

---

## Extraction Contract

Input:

- WeChat article URL
- Current ingest date, used for the `.raw/articles/` filename and `fetched` field

Output:

- `.raw/articles/[slug]-[YYYY-MM-DD].md`
- Frontmatter:

```markdown
---
source_url: [url]
fetched: [YYYY-MM-DD]
title: "[extracted title]"
account: "[extracted public-account name]"
published: [YYYY-MM-DD]
---
```

Body:

```markdown
# [extracted title]

[cleaned article prose]
```

---

## Fetch Strategy

Fetch the article HTML with `curl`, not generic WebFetch:

- Use `-L --compressed -sS`
- Use a desktop browser `User-Agent`
- Use `Accept-Language: zh-CN,zh;q=0.9,en;q=0.8`
- Save to a temp file such as `/tmp/wechat-article.html`

Reason: WeChat often includes the full article body in the initial HTML under `#js_content`, but generic fetchers may return noisy script-heavy output or fail to surface the body.

---

## Fields To Extract

Check the HTML for these fields:

```bash
rg -n "msg_title|js_content|nickname|ct =" /tmp/wechat-article.html | sed -n '1,80p'
```

Expected fields:

- `var msg_title = ...` — article title
- `var nickname = ...` — public-account name
- `var ct = "..."` — Unix publish timestamp
- `id="js_content"` — article body HTML

Convert `ct` to `YYYY-MM-DD` for `published`.

---

## Body Cleaning Rules

Extract the inner HTML of `#js_content`, then:

- Treat `br`, `p`, `section`, headings, blockquotes, and list items as paragraph breaks.
- Decode HTML entities, including numeric entities.
- Strip remaining tags.
- Collapse repeated whitespace inside a line.
- Preserve paragraph breaks.
- Preserve images as `![alt]` placeholders unless image OCR is needed.
- Do not download every image by default; only download relevant `data-src` images when the image carries meaningful text, diagrams, or data.

The resulting body should be mostly article prose, not JavaScript, CSS, navigation, comments, or ad boilerplate.

---

## Slug Rule

For `/s/<id>` links, use the article id lowercased as the slug:

```text
https://mp.weixin.qq.com/s/L11cw9ecXrmwbX4CV5P9yA
=> l11cw9ecxrmwbx4cv5p9ya
```

Save as:

```text
.raw/articles/[slug]-[YYYY-MM-DD].md
```

---

## Quality Gate

Before returning to the main ingest flow:

- Confirm the source file exists in `.raw/articles/`.
- Confirm the title/account/published fields were extracted when present.
- Confirm body length is non-trivial and content is human-readable prose.
- If `#js_content` is missing or empty, stop this sub-processor and use the ordinary URL fallback.
- If important article content is only inside images, run Image / Vision Ingestion for those images and link the results from the source summary.

After the quality gate passes, proceed with Single Source Ingest on the saved `.raw/articles/` file.

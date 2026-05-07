# claude-obsidian — Claude + Obsidian Wiki Vault

This folder is both a Claude Code plugin and an Obsidian vault.

**Plugin name:** `claude-obsidian`
**Skills:** `/wiki`, `/wiki-ingest`, `/wiki-query`, `/wiki-lint`
**Vault path:** This directory (open in Obsidian directly)

## What This Vault Is For

This vault demonstrates the LLM Wiki pattern — a persistent, compounding knowledge base for Claude + Obsidian. Drop any source, ask any question, and the wiki grows richer with every session.

## Vault Structure

```
.raw/           source documents — immutable, Claude reads but never modifies
wiki/           Claude-generated knowledge base
_templates/     Obsidian Templater templates
_attachments/   images and PDFs referenced by wiki pages
```

## How to Use

Drop a source file into `.raw/`, then tell Claude: "ingest [filename]".

Ask any question. Claude reads the index first, then drills into relevant pages.

Run `/wiki` to scaffold a new vault or check setup status.

Run "lint the wiki" every 10-15 ingests to catch orphans and gaps.

## Personal Wiki Conventions

This vault is being used as a personal knowledge base. Keep folder names in English for tool compatibility, but write page titles and body content in Chinese when the user's material is Chinese.

### Todo and Goal Linking

Todos should live in the page that owns their context:

- Learning tasks go in `wiki/learning/`
- Project tasks go in `wiki/projects/`
- Long-term outcomes go in `wiki/goals/`
- Ongoing life-maintenance tasks go in `wiki/areas/`
- Decisions go in `wiki/decisions/`
- Completed reviews and patterns go in `wiki/reflections/`

When a todo supports a goal, link both directions:

1. In the task-owning page, add `目标：[[goals/Goal Page]]` near the top, or a `## 关联目标` section if there are multiple goals.
2. In the goal page, maintain a `## 关联任务` section that links back to the learning/project/area page and lists the next actions that matter for the goal.
3. Do not duplicate every tiny checkbox everywhere. The detailed checklist stays in the owning page; the goal page keeps the goal-level view.
4. When the user says "todo" without specifying a goal, classify it first. If a likely goal exists, link it. If not, leave it in the owning page and add it to `wiki/hot.md` as an open thread when it is currently important.

## Cross-Project Access

To reference this wiki from another Claude Code project, add to that project's CLAUDE.md:

```markdown
## Wiki Knowledge Base
Path: /path/to/this/vault

When you need context not already in this project:
1. Read wiki/hot.md first (recent context, ~500 words)
2. If not enough, read wiki/index.md
3. If you need domain specifics, read wiki/<domain>/_index.md
4. Only then read individual wiki pages

Do NOT read the wiki for general coding questions or things already in this project.
```

## Plugin Skills

| Skill | Trigger |
|-------|---------|
| `/wiki` | Setup, scaffold, route to sub-skills |
| `ingest [source]` | Single or batch source ingestion |
| `query: [question]` | Answer from wiki content |
| `lint the wiki` | Health check |
| `/save` | File the current conversation as a structured wiki note |
| `/autoresearch [topic]` | Autonomous research loop: search, fetch, synthesize, file |
| `/canvas` | Visual layer: add images, PDFs, notes to Obsidian canvas |

## MCP (Optional)

If you configured the MCP server, Claude can read and write vault notes directly.
See `skills/wiki/references/mcp-setup.md` for setup instructions.

---
source_type: github-repo
url: https://github.com/rohitg00/agentmemory
repo: rohitg00/agentmemory
stars: 7121
language: TypeScript
license: Apache-2.0
fetched_at: 2026-05-14
---

# agentmemory — Persistent Memory for AI Coding Agents

> "#1 Persistent memory for AI coding agents based on real-world benchmarks"
> Built on iii engine. Works with Claude Code, Cursor, Gemini CLI, Codex CLI, Hermes, OpenClaw, pi, OpenCode, and any MCP client.

## Key Stats

- R@5 95.2% on LongMemEval-S (ICLR 2025, 500 questions)
- 92% fewer tokens (~170K/yr vs 19.5M+)
- 51 MCP tools
- 12 auto hooks
- 0 external DBs
- 827 tests passing

## Installation

```bash
npx @agentmemory/agentmemory
```

Claude Code: `/plugin marketplace add rohitg00/agentmemory` then `/plugin install agentmemory`

## Architecture

### 4-Tier Memory Consolidation

| Tier | What | Analogy |
|------|------|---------|
| Working | Raw observations from tool use | Short-term memory |
| Episodic | Compressed session summaries | "What happened" |
| Semantic | Extracted facts and patterns | "What I know" |
| Procedural | Workflows and decision patterns | "How to do it" |

Memories decay over time (Ebbinghaus curve). Frequently accessed memories strengthen. Stale memories auto-evict. Contradictions are detected and resolved.

### Triple-Stream Retrieval

| Stream | What |
|---|---|
| BM25 | Stemmed keyword matching with synonym expansion |
| Vector | Cosine similarity over dense embeddings |
| Graph | Knowledge graph traversal via entity matching |

Fused with Reciprocal Rank Fusion (RRF, k=60). Session-diversified (max 3 results per session).

### Memory Pipeline

```
PostToolUse hook fires
  -> SHA-256 dedup (5min window)
  -> Privacy filter (strip secrets, API keys)
  -> Store raw observation
  -> LLM compress -> structured facts + concepts + narrative
  -> Vector embedding (6 providers + local)
  -> Index in BM25 + vector

Stop / SessionEnd hook fires
  -> Summarize session
  -> Knowledge graph extraction
  -> Slot reflection

SessionStart hook fires
  -> Load project profile (top concepts, files, patterns)
  -> Hybrid search (BM25 + vector + graph)
  -> Token budget (default: 2000 tokens)
  -> Inject into conversation
```

### Ports

- 3111: API/REST (104 endpoints)
- 3113: Real-time viewer
- 3114: iii console

## vs Competitors

| | agentmemory | mem0 (53K⭐) | Letta/MemGPT (22K⭐) | Built-in (CLAUDE.md) |
|---|---|---|---|---|
| Retrieval R@5 | 95.2% | 68.5% | 83.2% | N/A |
| Auto-capture | 12 hooks | Manual add() | Agent self-edits | Manual |
| Search | BM25+Vector+Graph RRF | Vector+Graph | Vector | Load everything |
| External deps | None (SQLite+iii) | Qdrant/pgvector | Postgres+vector | None |
| Memory lifecycle | 4-tier+decay+auto-forget | Passive extraction | Agent-managed | Manual |
| Token/session | ~1,900 tokens | Varies | Core memory in context | 22K+ at 240 obs |

## Key Features

- Session replay: scrub through timeline of prompts/tool calls/results
- JSONL import: bring in existing Claude Code transcripts
- Team memory: namespaced shared + private across team members
- Citation provenance: trace any memory back to source observations
- Git snapshots: version, rollback, and diff memory state
- Privacy first: API keys, secrets, `<private>` tags stripped before storage
- Self-healing: circuit breaker, provider fallback chain, health monitoring
- Claude bridge: bi-directional sync with MEMORY.md

## iii Engine

Replaces Express, SQLite+pgvector, SSE, pm2, Prometheus with a single primitive system.
Repo: https://github.com/iii-hq/iii
agentmemory pins iii-engine to v0.11.2.

## Context

The gist (1200 stars / 172 forks) extends Karpathy's LLM Wiki pattern with confidence scoring, lifecycle, knowledge graphs, and hybrid search. agentmemory is the implementation.

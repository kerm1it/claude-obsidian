---
source_url: https://github.com/colbymchenry/codegraph
fetched: 2026-06-29
---
# CodeGraph

CodeGraph is a pre-indexed code knowledge graph that automatically syncs on code changes. It's designed to supercharge AI coding agents — Claude Code, Cursor, Codex, OpenCode, Hermes Agent, Gemini CLI, Antigravity IDE, and Kiro — by providing "surgical context, not a file-by-file search." The tool is 100% local, uses an SQLite database, and sends no data off the machine.

## Repository Info

- **GitHub**: colbymchenry/codegraph
- **Stars**: ~55.8K
- **Language**: TypeScript (92.2%)
- **License**: MIT
- **Creator**: Colby McHenry
- **Latest Release**: v1.1.3 (June 2026)

## Key Features

- **Surgical Context**: One tool call returns entry points, related symbols, and code snippets
- **Full-Text Search**: Powered by FTS5 across the entire codebase
- **Impact Analysis**: Traces callers, callees, and full impact radius of any symbol
- **Always Fresh**: Native OS file watchers (FSEvents/inotify/ReadDirectoryChangesW) with debounced auto-sync
- **20+ Languages**: TypeScript, JavaScript, Python, Go, Rust, Java, C#, PHP, Ruby, C, C++, Objective-C, Swift, Kotlin, Scala, Dart, Lua, Luau, R, Svelte, Vue, Astro, Liquid, Pascal/Delphi
- **Framework-aware Routes**: Recognizes web-framework routing across 17 frameworks
- **Mixed iOS/React Native/Expo Bridging**: Crosses language boundaries
- **100% Local**: No API keys, no external services, SQLite only

## Architecture (Four Layers)

1. **Extraction**: tree-sitter parses source code into ASTs; language-specific queries extract nodes (functions, classes, methods) and edges (calls, imports, extends, implements)
2. **Storage**: Everything placed in a local SQLite database (`.codegraph/codegraph.db`) with FTS5 full-text search
3. **Resolution**: References resolved post-extraction — function calls to definitions, imports to source files, class inheritance, framework-specific patterns
4. **Auto-Sync**: Native OS file events trigger re-indexing after a debounce window; stale-content banners during pending syncs

## Benchmark Results (v1.0, Re-validated 2026-06-02)

Across 7 real-world open-source codebases, Claude Opus 4.8:

| Codebase | Language | Size | Tool Calls | Time | Tokens | Cost |
|---|---|---|---|---|---|---|
| VS Code | TypeScript | ~10k files | 81% fewer | 11% faster | 64% fewer | 18% cheaper |
| Excalidraw | TypeScript | ~640 files | 40% fewer | 27% faster | 25% fewer | even |
| Django | Python | ~3k files | 77% fewer | 13% faster | 60% fewer | 8% cheaper |
| Tokio | Rust | ~790 files | 57% fewer | 18% faster | 38% fewer | even |
| OkHttp | Java | ~645 files | 50% fewer | 31% faster | 54% fewer | 25% cheaper |
| Gin | Go | ~110 files | 44% fewer | 24% faster | 23% fewer | 19% cheaper |
| Alamofire | Swift | ~110 files | 58% fewer | 33% faster | 64% fewer | 40% cheaper |

Aggregate: 58% fewer tool calls, 22% faster, file reads cut to ~zero, 47% fewer tokens, ~16% cheaper.

## Installation

```bash
# Shell installer (no Node.js required)
curl -fsSL https://raw.githubusercontent.com/colbymchenry/codegraph/main/install.sh | sh

# npm
npm i -g @colbymchenry/codegraph

# Setup
codegraph install
codegraph init
```

## MCP Integration

Single primary MCP tool `codegraph_explore` — returns verbatim source grouped by file, call paths between symbols, and blast-radius summaries. Additional tools available but unlisted by default.

## Cross-File Coverage

TypeScript/JS 95.8%, Python 100%, Go 96.6%, Rust 86.7%, Java 93.3%, PHP 100%, Ruby 100%, Swift 95.3%, Kotlin 96.2%, and others ranging from 74-100%.

## Limitations

- First-time indexing costs time and disk space on large repos
- Static analysis misses dynamic imports, reflection, dependency injection
- Benchmark numbers depend on model, prompts, repo structure, and task type
- MCP access needs governance

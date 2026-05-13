---
source_url: https://github.com/thedotmack/claude-mem
fetched: 2026-05-13
---

# claude-mem

**GitHub**: https://github.com/thedotmack/claude-mem  
**Author**: Alex Newman (@thedotmack)  
**Stars**: 75,423  
**Version**: 13.2.0 (package.json; README badge shows 6.5.0)  
**Language**: TypeScript  
**License**: Apache 2.0

**Description**: Persistent Context Across Sessions for Every Agent – Captures everything your agent does during sessions, compresses it with AI, and injects relevant context back into future sessions. Works with Claude Code, OpenClaw, Codex, Gemini, Hermes, Copilot, OpenCode + More

---

## README Content

[Full README fetched from GitHub — see source for full content]

Key points extracted:

### What it does
Claude-Mem seamlessly preserves context across sessions by automatically capturing tool usage observations, generating semantic summaries, and making them available to future sessions. Enables Claude to maintain continuity of knowledge about projects even after sessions end or reconnect.

### Installation
```bash
npx claude-mem install
# or
/plugin marketplace add thedotmack/claude-mem
/plugin install claude-mem
```

### Core Components
1. **5 Lifecycle Hooks** - SessionStart, UserPromptSubmit, PostToolUse, Stop, SessionEnd (6 hook scripts)
2. **Smart Install** - Cached dependency checker
3. **Worker Service** - HTTP API on port 37777 with web viewer UI, managed by Bun
4. **SQLite Database** - Stores sessions, observations, summaries
5. **mem-search Skill** - Natural language queries with progressive disclosure
6. **Chroma Vector Database** - Hybrid semantic + keyword search

### MCP Search Tools (3-Layer Workflow)
1. `search` - Get compact index with IDs (~50-100 tokens/result)
2. `timeline` - Get chronological context around interesting results
3. `get_observations` - Fetch full details ONLY for filtered IDs (~500-1,000 tokens/result)
→ ~10x token savings by filtering before fetching details

### Key Features
- Persistent Memory across sessions
- Progressive Disclosure - layered memory retrieval with token cost visibility
- Skill-Based Search (mem-search)
- Web Viewer UI at http://localhost:37777
- Privacy Control via `<private>` tags
- Citations via observation IDs
- Endless Mode (beta) - biomimetic memory architecture
- OpenClaw Gateway integration
- Multi-platform: Claude Code, OpenClaw, Codex, Gemini, Hermes, Copilot, OpenCode

### Tech Stack
- Runtime: Bun
- Storage: SQLite (bundled)
- Vector DB: Chroma
- Package: npm / Claude Code plugin marketplace
- Key deps: @anthropic-ai/claude-agent-sdk, @modelcontextprotocol/sdk, bullmq, express, better-auth

### Configuration
Settings in `~/.claude-mem/settings.json`  
Mode: `CLAUDE_MEM_MODE` (e.g., `code--zh` for Chinese)

### Social
- X: @Claude_Memory
- Discord: discord.com/invite/J4wttp9vDu
- $CMEM: Solana token (community catalyst, embraced by author)

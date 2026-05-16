---
source_url: https://github.com/tinyhumansai/openhuman
fetched: 2026-05-16
---

# OpenHuman — GitHub README

**Repo**: tinyhumansai/openhuman  
**Stars**: 10,137 | **Forks**: 863  
**Language**: Rust (Tauri desktop shell)  
**License**: GPL-3.0  
**Status**: Early Beta  
**Homepage**: https://tinyhumans.ai/openhuman  
**Creator**: @senamakel  

## Description

OpenHuman is your Personal AI super intelligence. Private, Simple and extremely powerful.

## What is OpenHuman?

OpenHuman is an open-source agentic assistant designed to integrate with you in your daily life.

- **Simple, UI-first & Human**: A clean desktop experience and short onboarding paths take you from install to a working agent in a few clicks — no config-first setup, no terminal required. The agent has a face: a desktop mascot that speaks, reacts to its surroundings, joins your Google Meets as a real participant, remembers you across weeks, and keeps thinking in the background even when you've stopped typing.

- **118+ third-party integrations with auto-fetch**: plug into Gmail, Notion, GitHub, Slack, Stripe, Calendar, Drive, Linear, Jira and the rest of your stack with one-click OAuth. Every connection is exposed to the agent as a typed tool, and every twenty minutes the core walks each active connection and pulls fresh data into the memory tree. No prompts, no polling loops you have to write, so the agent already has tomorrow's context this morning.

- **Memory Tree + Obsidian Wiki**: a local-first knowledge base built from your data and your activity. Everything you connect is canonicalized into ≤3k-token Markdown chunks, scored, and folded into hierarchical summary trees stored in SQLite on your machine. The same chunks land as .md files in an Obsidian-compatible vault you can open, browse and edit, inspired by Karpathy's obsidian-wiki workflow.

- **Batteries included**: web search, a web-fetch scraper, a full coder toolset (filesystem, git, lint, test, grep), and native voice (STT in, ElevenLabs TTS out, mascot lip-sync, live Google Meet agent) are wired in by default. Model routing sends each task to the right LLM (reasoning, fast, or vision) under one subscription. Optional local AI via Ollama for on-device workloads.

- **Smart token compression (TokenJuice)**: every tool call, scrape result, email body, and search payload is run through a token compression layer before it touches any LLM Model. HTML is converted to Markdown, long URLs are shortened, non-ASCII characters are removed etc... You get the same information but at a fraction of the tokens. Reducing cost & latency by up to 80%.

- **Messaging channels and privacy & security**: inbound/outbound across the channels you already use, with workflow data that stays on device, encrypted locally, treated as yours.

## Context in minutes, not weeks

OpenHuman is the first agent harness that gets to know you in minutes. Inspired by Karpathy's LLM Knowledgebase. Most agents start cold. Hermes learns by watching you work; OpenClaw waits for plugins to ferry context in. Either way, you spend days or weeks before the agent knows enough about your stack to be genuinely useful.

OpenHuman skips the wait. Connect your accounts, let auto-fetch pull data locally on a 20-minute loop, and then have Memory Trees compress everything into Markdown files stored intelligently in a Karpathy-style Obsidian wiki.

In just one sync pass, the agent has full (compressed) context of your inbox, your calendar, your repos, your docs, your messages. No training period. No "give it a few weeks." It becomes you, controlled by you.

Already self-host agentmemory across other coding agents? OpenHuman ships an optional Memory backend that proxies to it — set `memory.backend = "agentmemory"` in config.toml and the same durable store powers OpenHuman alongside Claude Code, Cursor, Codex, and OpenCode.

## OpenHuman vs Other Agent Harnesses

|                     | Claude Cowork     | OpenClaw          | Hermes Agent      | OpenHuman                          |
| ------------------- | ----------------- | ----------------- | ----------------- | ---------------------------------- |
| **Open-source**     | Proprietary       | MIT               | MIT               | GNU                                |
| **Simple to start** | Desktop + CLI     | Terminal-first    | Terminal-first    | Clean UI, minutes                  |
| **Cost**            | Sub + add-ons     | BYO models        | BYO models        | One sub + TokenJuice               |
| **Memory**          | Chat-scoped       | Plugin-reliant    | Self-learning     | Memory Tree + Obsidian vault       |
| **Integrations**    | Few connectors    | BYO               | BYO               | 118+ via OAuth                     |
| **Auto-fetch**      | None              | None              | None              | 20-min sync into memory            |
| **API sprawl**      | Extra keys        | BYOK              | Multi-vendor      | One account                        |
| **Model routing**   | Single model      | Manual            | Manual            | Built-in                           |
| **Native tools**    | Code-only         | Code-only         | Code-only         | Code + search + scraper + voice    |

## Tech Stack

- **Desktop shell**: Rust + Tauri
- **Storage**: SQLite (local, encrypted)
- **Voice**: ElevenLabs TTS, STT input, mascot lip-sync
- **Token compression**: TokenJuice layer (HTML→MD, URL shortening, non-ASCII removal)
- **Memory backend**: Local SQLite OR optional agentmemory proxy
- **Model routing**: Reasoning / fast / vision LLM selection per task
- **Local AI**: Optional Ollama integration

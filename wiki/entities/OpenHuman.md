---
id: c-000105
address: c-000105
type: entity
entity_type: open-source-product
title: "OpenHuman"
aka: ["OpenHuman"]
parent: "[[entities/TinyHumansAI]]"
url: https://github.com/tinyhumansai/openhuman
created: 2026-05-16
tags:
  - ai-agent
  - open-source
  - desktop-app
  - memory
  - rust
  - tauri
status: active
---

# OpenHuman

开源桌面 AI 助理。**10,137 ⭐ · GPL-3.0 · Rust + Tauri · Early Beta**

> "Your Personal AI super intelligence. Private, Simple and extremely powerful."

由 [[people/Senamakel]] 创建，[[entities/TinyHumansAI]] 出品。

---

## 核心主张

**让 agent 在几分钟内了解你，而不是几周。**

大多数 agent harness 冷启动：OpenClaw 等待插件传入上下文；Hermes 通过观察工作逐步学习。OpenHuman 跳过等待期——连接账户、让 [[concepts/记忆自动拉取|Auto-fetch]] 每 20 分钟拉一次数据，Memory Tree 即刻压缩为 Karpathy 风格的 Obsidian wiki。

灵感直接来源：[Karpathy's LLM Knowledgebase workflow](https://x.com/karpathy/status/2039805659525644595)。

---

## 核心功能

| 功能 | 描述 |
|------|------|
| **Desktop Mascot** | 有脸的 AI：桌面吉祥物，能说话、加入 Google Meet、后台持续思考 |
| **118+ OAuth 集成** | Gmail、Notion、GitHub、Slack、Stripe、Calendar、Drive、Linear、Jira 等一键接入 |
| **[[concepts/记忆自动拉取\|Auto-fetch]]** | 每 20 分钟遍历所有活跃连接，拉新数据入 Memory Tree |
| **[[concepts/MemoryTree\|Memory Tree]]** | ≤3k-token Markdown 块 → 层级摘要树 → SQLite 本地存储 + Obsidian vault |
| **[[concepts/TokenJuice]]** | Token 压缩层：HTML→MD、URL 缩短、非 ASCII 移除，成本/延迟最多降 80% |
| **模型路由** | 内置 reasoning/fast/vision 路由，一个订阅覆盖多模型 |
| **原生工具** | Web 搜索 + 爬取 + 完整 Coder 工具（fs/git/lint/test/grep）+ ElevenLabs 语音 |
| **AgentMemory 后端** | 可选：将 [[entities/AgentMemory]] 作为统一记忆后端，与 Claude Code/Cursor/Codex 共享 |
| **本地优先** | 工作流数据留在设备，加密存储，不上传 |

---

## 技术栈

- **桌面壳**：Rust + Tauri（跨平台，macOS / Windows / Linux）
- **存储**：SQLite（本地加密）
- **语音**：ElevenLabs TTS + STT 输入 + 吉祥物口型同步
- **Token 压缩**：TokenJuice（自研预处理层）
- **本地 AI**：可选 Ollama 集成

---

## 竞品定位

| | Claude Cowork | OpenClaw | Hermes | **OpenHuman** |
|--|--|--|--|--|
| 开源 | ✗ | MIT | MIT | GPL-3.0 |
| 记忆 | 会话范围 | 插件依赖 | 自我学习 | Memory Tree + Obsidian |
| 自动拉取 | ✗ | ✗ | ✗ | 每 20 分钟 |
| 集成 | 少量 | BYO | BYO | 118+ OAuth |
| Token 压缩 | ✗ | ✗ | ✗ | TokenJuice（-80%） |

---

## 关联

- [[entities/TinyHumansAI]] — 母公司
- [[people/Senamakel]] — 创作者
- [[concepts/TokenJuice]] — Token 压缩
- [[concepts/记忆自动拉取]] — Auto-fetch
- [[concepts/MemoryTree]] — 记忆知识图谱
- [[entities/AgentMemory]] — 可选记忆后端
- [[entities/ClaudeCowork]] — 竞品
- [[entities/OpenClaw]] — 竞品
- [[sources/openhuman-2026-05-16|来源：GitHub README]]

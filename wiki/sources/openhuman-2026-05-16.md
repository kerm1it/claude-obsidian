---
id: c-000104
address: c-000104
type: source
title: "OpenHuman — GitHub README（2026-05-16）"
source_url: https://github.com/tinyhumansai/openhuman
fetched: 2026-05-16
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

# OpenHuman — GitHub README（2026-05-16）

**来源**：https://github.com/tinyhumansai/openhuman  
**抓取日期**：2026-05-16  
**Stars**：10,137 | **Forks**：863  
**License**：GPL-3.0 | **状态**：Early Beta  

---

## 核心定位

[[entities/OpenHuman]] 是一个开源桌面 AI 助理，定位为"个人 AI 超级智能"（Personal AI super intelligence）。口号：**Private, Simple and extremely powerful**。

与其他 agent harness 的根本差异在于：**让 agent 在几分钟内了解你，而不是几周**。

> "OpenHuman is the first agent harness that gets to know you in minutes."

灵感来源：Karpathy 的 [LLM Knowledgebase / Obsidian wiki workflow](https://x.com/karpathy/status/2039805659525644595)。

---

## 核心功能

### 1. Desktop 桌面 Mascot

- 有"脸"的 AI 助理：桌面吉祥物形象，能说话、对周围环境做出反应
- 可作为真实参与者**加入 Google Meets**
- 在用户停止输入时仍在后台持续思考
- ElevenLabs TTS 语音输出 + 口型同步（lip-sync）

### 2. 118+ 第三方集成（一键 OAuth）

覆盖：Gmail、Notion、GitHub、Slack、Stripe、Calendar、Google Drive、Linear、Jira 等。

每个连接以类型化工具（typed tool）形式暴露给 agent，无需手写 polling 循环。

→ 详见 [[concepts/记忆自动拉取]]

### 3. Memory Tree + Obsidian Wiki

- 所有连接的数据被规范化为 **≤3k-token Markdown 块**，打分后折叠进层级摘要树
- 存储：本机 **SQLite**（加密，数据不离设备）
- 同时落地为 `.md` 文件，构成一个可在 Obsidian 中打开、浏览、编辑的知识库
- Karpathy-style obsidian wiki 实现

→ 详见 [[concepts/MemoryTree]]

### 4. TokenJuice — 智能 Token 压缩

每个工具调用、爬取结果、邮件正文、搜索载荷在进入 LLM 前都经过压缩层处理：
- HTML → Markdown 转换
- 长 URL 缩短
- 非 ASCII 字符移除

**效果**：成本与延迟最多降低 **80%**。

→ 详见 [[concepts/TokenJuice]]

### 5. Auto-fetch — 自动定时拉取

每 **20 分钟**一次循环，遍历所有活跃连接，将最新数据拉入 Memory Tree。

实现"agent 今早已经知道你明天的日程"的效果。

→ 详见 [[concepts/记忆自动拉取]]

### 6. 内置工具集（开箱即用）

- Web 搜索
- Web 爬取（scraper）
- 完整 Coder 工具集（filesystem、git、lint、test、grep）
- 原生语音（STT 输入 + ElevenLabs TTS 输出）
- 模型路由（reasoning / fast / vision，按任务自动选择）
- 可选 Ollama 本地 AI

### 7. AgentMemory 后端支持

已在其他 coding agent（Claude Code、Cursor、Codex、OpenCode）中使用 [[entities/AgentMemory]] 的用户，可在 `config.toml` 设置：

```toml
memory.backend = "agentmemory"
```

同一个持久化存储同时驱动 OpenHuman 和其他 agent。

---

## 竞品对比表

|                | Claude Cowork  | OpenClaw       | Hermes Agent   | **OpenHuman**                   |
|----------------|----------------|----------------|----------------|----------------------------------|
| 开源           | ✗ 闭源         | ✓ MIT          | ✓ MIT          | ✓ GPL-3.0                       |
| 上手难度       | 桌面+CLI       | 终端优先       | 终端优先       | 干净 UI，几分钟即用              |
| 费用           | 订阅+附加费    | BYO 模型       | BYO 模型       | 单一订阅 + TokenJuice 降费       |
| 记忆           | 会话范围       | 依赖插件       | 自我学习       | Memory Tree + Obsidian vault     |
| 集成数量       | 少数连接器     | BYO            | BYO            | 118+ OAuth                       |
| 自动拉取       | ✗              | ✗              | ✗              | ✓ 20分钟同步                     |
| API 分散度     | 额外密钥       | BYOK           | 多供应商       | ✓ 单一账户                       |
| 模型路由       | 单模型         | 手动           | 手动           | ✓ 内置                           |
| 原生工具       | 仅代码         | 仅代码         | 仅代码         | 代码+搜索+爬虫+语音              |

---

## 技术栈

| 层 | 技术 |
|----|------|
| 桌面壳 | Rust + Tauri |
| 存储 | SQLite（本地加密） |
| 语音 | ElevenLabs TTS + STT |
| Token 压缩 | TokenJuice（自研层） |
| 记忆后端 | 本地 SQLite / agentmemory 代理（可选） |
| 模型路由 | 内置（reasoning/fast/vision） |
| 本地 AI | Ollama（可选） |

---

## 创始人 / 创作者

[[people/Senamakel]]（@senamakel）— TinyHumans AI 创始人

---

## 关联

- [[entities/OpenHuman]] — 实体页
- [[entities/TinyHumansAI]] — 母公司/组织
- [[people/Senamakel]] — 创作者
- [[concepts/TokenJuice]] — Token 压缩层
- [[concepts/记忆自动拉取]] — Auto-fetch 机制
- [[concepts/MemoryTree]] — 本地知识图谱
- [[entities/AgentMemory]] — 可选记忆后端
- [[entities/ClaudeCowork]] — 竞品对比
- [[entities/OpenClaw]] — 竞品对比

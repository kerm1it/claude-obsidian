---
address: c-000075
type: source
title: "claude-mem — 跨会话持久记忆系统（thedotmack，2026-05-13）"
created: 2026-05-13
updated: 2026-05-13
tags:
  - ai-agent
  - memory
  - claude-code
  - open-source
  - plugin
status: active
source_url: "https://github.com/thedotmack/claude-mem"
source_kind: github
entities:
  - "[[entities/ClaudeMem]]"
concepts:
  - "[[concepts/渐进式上下文注入]]"
  - "[[concepts/AgentMemoryAPI]]"
related:
  - "[[sources/gbrain-2026-05-11]]"
  - "[[sources/memory-dreaming-self-learning-agents-2026-05-11]]"
---

# claude-mem — 跨会话持久记忆系统（thedotmack，2026-05-13）

**项目：** [[entities/ClaudeMem]]  
**作者：** Alex Newman（@thedotmack）  
**GitHub：** https://github.com/thedotmack/claude-mem  
**Stars：** ⭐ 75,423  
**版本：** 13.2.0 | **语言：** TypeScript | **协议：** Apache 2.0

---

## 核心定位

> "跨会话持久上下文系统——自动捕获 Agent 的每一次工具调用，用 AI 压缩后，注入到未来会话中。"

claude-mem 解决的是 AI Agent 的"失忆"问题：每次新会话都从零开始，丢失所有历史上下文。它的策略是**捕获 → 压缩 → 注入**，实现跨会话的知识持续性。

---

## 架构：六大组件

### 1. 5 种生命周期钩子

| 钩子 | 触发时机 |
|---|---|
| SessionStart | 会话开始，注入历史上下文 |
| UserPromptSubmit | 用户提交 prompt |
| PostToolUse | 每次工具调用后，捕获观察 |
| Stop | 会话暂停 |
| SessionEnd | 会话结束，生成摘要 |

→ 与 Lucas 演讲中的 [[domains/Claude-Code]] pre/post tool use hooks 直接对应。

### 2. Worker Service
- HTTP API（port 37777）
- Web Viewer UI（实时记忆流）
- 由 Bun 管理进程
- 10 个搜索端点

### 3. SQLite 数据库
存储：sessions、observations（工具调用快照）、summaries

### 4. Chroma 向量数据库
混合检索：语义向量 + 关键词全文检索（与 [[concepts/混合检索RRF]] 同类方案）

### 5. mem-search Skill
自然语言查询历史，支持渐进式披露（[[concepts/渐进式上下文注入]]）

### 6. MCP 搜索工具（3 层工作流）

```
search(query) → 获取紧凑索引（~50-100 tokens/条）
    ↓
timeline(id) → 获取时间线上下文
    ↓
get_observations(ids) → 获取完整详情（~500-1000 tokens/条）
```

**效果：节省约 10x tokens**——先过滤再拉取详情。

---

## 渐进式上下文注入（[[concepts/渐进式上下文注入]]）

claude-mem 的核心设计哲学：**不是把所有历史记忆一次性塞入上下文**，而是分层、按需、带 token 成本可视化地注入。

- 第一层：紧凑索引（ID + 摘要）
- 第二层：时间线上下文（发生了什么前后）
- 第三层：完整观察详情（仅对筛选后的 ID 拉取）

---

## 安装

```bash
# 方式一：npx
npx claude-mem install

# 方式二：Claude Code 插件市场
/plugin marketplace add thedotmack/claude-mem
/plugin install claude-mem

# OpenClaw Gateway
curl -fsSL https://install.cmem.ai/openclaw.sh | bash

# Gemini CLI
npx claude-mem install --ide gemini-cli
```

---

## 支持的平台

Claude Code、[[entities/OpenClaw]]、Codex、Gemini CLI、Hermes、Copilot、OpenCode

---

## Beta 功能：Endless Mode

"仿生记忆架构"——用于超长会话的实验性记忆模式，通过 Web Viewer UI 切换（`http://localhost:37777` → Settings）。

---

## 配置

文件：`~/.claude-mem/settings.json`  
支持多语言模式：`CLAUDE_MEM_MODE: "code--zh"`（简体中文）

关键依赖：`@anthropic-ai/claude-agent-sdk`、`@modelcontextprotocol/sdk`、Chroma、SQLite、Bun

---

## 与生态系统的关系

| 系统 | 异同 |
|---|---|
| [[entities/GBrain]] | 同为 Agent 记忆系统；GBrain 更完整（Compiled Truth + Dream Cycle + RRF），claude-mem 更轻量易装（一条命令） |
| [[concepts/AgentMemoryAPI]]（Anthropic） | 官方 Memory API 是云端服务；claude-mem 是本地插件，互补而非竞争 |
| [[concepts/AnthropicDreaming]] | Dreaming 是离线批处理；claude-mem 是实时捕获 + 会话注入 |
| [[concepts/DreamCycle]]（GBrain） | 夜间维护维度；claude-mem 偏向实时会话维度 |

---

## 关联

- [[entities/ClaudeMem]] — 实体页面
- [[concepts/渐进式上下文注入]] — 核心设计模式
- [[entities/GBrain]] — 同类对比
- [[concepts/AgentMemoryAPI]] — Anthropic 官方记忆 API
- [[concepts/混合检索RRF]] — 检索策略同构
- [[sources/gbrain-2026-05-11]] — GBrain 详细介绍
- [[sources/memory-dreaming-self-learning-agents-2026-05-11]] — Anthropic Memory + Dreaming

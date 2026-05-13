---
address: c-000076
type: entity
title: "claude-mem"
created: 2026-05-13
updated: 2026-05-13
tags:
  - ai-agent
  - memory
  - claude-code
  - open-source
  - plugin
status: active
related:
  - "[[entities/GBrain]]"
  - "[[entities/OpenClaw]]"
  - "[[concepts/渐进式上下文注入]]"
  - "[[concepts/AgentMemoryAPI]]"
  - "[[concepts/混合检索RRF]]"
---

# claude-mem

**类型：** 开源 Claude Code 插件 / AI Agent 记忆系统  
**作者：** Alex Newman（@thedotmack）  
**GitHub：** https://github.com/thedotmack/claude-mem  
**Stars：** ⭐ 75,423（2026-05-13）  
**版本：** 13.2.0 | **语言：** TypeScript | **协议：** Apache 2.0

---

## 核心定位

跨会话持久记忆系统。自动捕获 Agent 工具调用，AI 压缩后注入未来会话。单条安装命令，零配置启动。

---

## 技术架构

- **钩子**：5 种生命周期钩子（SessionStart/PostToolUse/SessionEnd 等）
- **存储**：SQLite（观察记录）+ Chroma（向量检索）
- **运行时**：Bun（Worker Service，port 37777）
- **检索**：3 层 MCP 工具（search → timeline → get_observations，节省 10x tokens）
- **核心模式**：[[concepts/渐进式上下文注入]]

---

## 与 GBrain 对比

| 维度 | claude-mem | [[entities/GBrain]] |
|---|---|---|
| 安装复杂度 | 一条命令 | 需要配置 |
| 记忆粒度 | 工具调用级别（observations） | 知识页面级别（Compiled Truth） |
| 维护机制 | 实时捕获 | 夜间 Dream Cycle |
| 检索 | 混合（Chroma） | 混合 RRF |
| 适用场景 | 轻量、快速接入 | 重型知识库管理 |

---

## 支持平台

Claude Code、[[entities/OpenClaw]]、Codex、Gemini CLI、Hermes、Copilot、OpenCode

---

## 来源

- [[sources/claude-mem-2026-05-13]]

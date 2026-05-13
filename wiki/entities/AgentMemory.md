---
type: entity
address: c-000079
title: "AgentMemory"
entity_type: open-source-tool
url: https://github.com/rohitg00/agentmemory
created: 2026-05-14
tags:
  - agent-memory
  - mcp
  - knowledge-graph
  - typescript
related:
  - "[[entities/ClaudeMem]]"
  - "[[entities/GBrain]]"
  - "[[concepts/四层记忆整合]]"
  - "[[concepts/AgentMemoryAPI]]"
  - "[[concepts/混合检索RRF]]"
---

# AgentMemory

rohitg00/agentmemory，GitHub，⭐ 7,121，TypeScript，Apache 2.0

AI 编码智能体持久记忆引擎。基于 [iii engine](https://github.com/iii-hq/iii) 构建，自称 "#1 Persistent memory for AI coding agents"。

## 核心参数

| 指标 | 数值 |
|---|---|
| Stars | 7,121 |
| 检索精度（R@5） | 95.2%（LongMemEval-S） |
| Token 节省 | 92%（~170K/yr vs 19.5M+） |
| MCP tools | 51 |
| 生命周期钩子 | 12 |
| 外部数据库依赖 | 0（内置 SQLite + iii engine） |

## 架构亮点

- **[[concepts/四层记忆整合]]**：Working → Episodic → Semantic → Procedural，类脑记忆层级
- **三流检索**：BM25 + Vector + Graph，RRF 融合（与 [[concepts/混合检索RRF]] 独立收敛）
- **12 hooks**：自动捕获全部工具调用，零手动配置
- **记忆衰减**：Ebbinghaus 曲线 + 矛盾检测 + 自动驱逐

## 兼容性

Claude Code、Cursor、Gemini CLI、Codex CLI、Hermes、OpenClaw、pi、OpenCode、Cline、Roo Code、Windsurf、Aider、Claude Desktop，以及任何 MCP 客户端。

安装：`npx @agentmemory/agentmemory`

Claude Code：`/plugin marketplace add rohitg00/agentmemory`

## 与同类对比

| | agentmemory | [[entities/ClaudeMem]] | [[entities/GBrain]] |
|---|---|---|---|
| Stars | 7.1K | 75K | 14.6K |
| 定位 | 全功能记忆引擎 | 轻量跨会话记忆 | 知识管理+Dream Cycle |
| 检索 | BM25+Vector+Graph+RRF | 3 层 MCP 流 | Compiled Truth+RRF |
| 安装成本 | 中（需 iii engine） | 低（1 条命令） | 高（完整系统） |
| 4 层记忆整合 | ✓ | ✗ | ✓（Dream Cycle） |
| 知识图谱 | ✓ | ✗ | 部分 |

## 来源

- [[sources/agentmemory-2026-05-13]]

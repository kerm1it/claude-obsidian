---
id: c-000110
address: c-000110
type: concept
title: "Memory Tree"
aliases: ["MemoryTree", "记忆树", "层级摘要树"]
created: 2026-05-16
tags:
  - memory
  - knowledge-graph
  - obsidian
  - local-first
  - agent
status: active
---

# Memory Tree

[[entities/OpenHuman]] 的本地知识图谱架构：将来自所有连接数据源的内容规范化、压缩、组织为**层级摘要树**，同时存储于 SQLite 和 Obsidian-兼容的 Markdown 文件中。

## 数据流

```
外部数据源（Gmail / GitHub / Notion / Slack / ...）
        ↓
  Auto-fetch 每 20 分钟拉取
        ↓
  TokenJuice 压缩（HTML→MD 等）
        ↓
  规范化为 ≤3k-token Markdown 块
        ↓
  打分（relevance scoring）
        ↓
  折叠进层级摘要树
        ↓
  ┌─────────────────────┐
  │  SQLite（本地加密） │  ← 结构化查询
  │  .md 文件（Obsidian）│  ← 可视化浏览
  └─────────────────────┘
```

## 存储双轨制

| 存储层 | 格式 | 用途 |
|--------|------|------|
| SQLite | 关系型，加密 | Agent 查询、结构化检索 |
| Obsidian vault | `.md` 文件 | 用户可视化浏览、手动编辑 |

用户可以直接在 Obsidian 中打开这个 vault，浏览和编辑 agent 生成的记忆——这正是 Karpathy LLM wiki 模式的核心价值。

## 灵感来源

直接引用：Karpathy 的 [obsidian-wiki workflow](https://x.com/karpathy/status/2039805659525644595)

> "The same chunks land as .md files in an Obsidian-compatible vault you can open, browse and edit, inspired by Karpathy's obsidian-wiki workflow."

与本项目（claude-obsidian）的关系：OpenHuman 的 Memory Tree 是 Karpathy 模式的**自动化扩展**——不需要用户手动摄入，agent 自动从连接的数据源构建 wiki。

## 与 AgentMemory 的关系

OpenHuman 可选 [[entities/AgentMemory]] 作为 Memory Tree 的后端：

```toml
# config.toml
memory.backend = "agentmemory"
```

设置后，Memory Tree 的持久化存储由 agentmemory 提供，同一份记忆可同时被 Claude Code、Cursor、Codex 访问。

## 与 GBrain / ClaudeMem 的对比

| 产品 | 记忆机制 | 本地性 | Obsidian 集成 |
|------|----------|--------|--------------|
| [[entities/GBrain]] | 图数据库 + 语义检索 | 云端 | ✗ |
| [[entities/ClaudeMem]] | 渐进式上下文注入 | 混合 | ✗ |
| [[entities/AgentMemory]] | 四层记忆（工作/情节/语义/程序） | 可自托管 | ✗ |
| **Memory Tree** | 层级摘要树 + SQLite | 完全本地 | ✓ |

## 关联

- [[entities/OpenHuman]] — 实现产品
- [[concepts/记忆自动拉取]] — 数据来源机制
- [[concepts/TokenJuice]] — 数据预处理层
- [[entities/AgentMemory]] — 可选后端
- [[entities/GBrain]] — 同类对比
- [[entities/ClaudeMem]] — 同类对比
- [[concepts/四层记忆整合]] — AgentMemory 的记忆模型
- [[sources/openhuman-2026-05-16|来源：GitHub README]]

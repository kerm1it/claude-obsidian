---
address: c-000212
type: source
title: "Built-in memory for Claude Managed Agents"
source_url: https://claude.com/blog/claude-managed-agents-memory
source_type: product-announcement
author: "Anthropic"
published: 2026-04-23
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - memory
  - managed-agents
  - self-learning
status: active
related:
  - "[[concepts/Dream与SelfImprovement工程原语]]"
  - "[[concepts/RAG与Memory边界]]"
---

# Built-in memory for Claude Managed Agents

**来源**：Claude Blog
**URL**：https://claude.com/blog/claude-managed-agents-memory

## 摘要

Anthropic 发布 Claude Managed Agents 的内置 memory，强调 agent 能跨 session 学习，并且 memory 以文件形式存储，开发者可通过 API 管理、导出和控制保留内容。

## 关键贡献

- Memory 直接挂载到 agent 文件系统，Claude 用常规文件工具读写。
- Memory 支持跨 session、跨 agent 共享学习。
- 官方案例强调 memory 的可观察、可控制和工作区作用域。

## 对 AI 知识体系的归属

- 主归属：4. 上下文与知识层
- 交叉链接：8. 自我改进与前沿层
- 作用：Dream 依赖 memory store；没有可治理 memory，self-improvement 只能停留在日志层。

## 关联

- [[concepts/Dream与SelfImprovement工程原语]]
- [[concepts/RAG与Memory边界]]
- [[Research: Dream 与 self-improvement 工程原语]]

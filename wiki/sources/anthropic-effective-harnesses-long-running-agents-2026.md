---
address: c-000205
type: source
title: "Effective harnesses for long-running agents"
source_url: https://www.anthropic.com/engineering/effective-harnesses-for-long-running-agents
source_type: article
author: "Anthropic"
published: 2025-11-26
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - agents
  - harness
  - long-running-agents
status: active
related:
  - "[[concepts/AgentHarness与TraceEval]]"
  - "[[concepts/上下文工程]]"
---

# Effective harnesses for long-running agents

**来源**：Anthropic Engineering
**URL**：https://www.anthropic.com/engineering/effective-harnesses-for-long-running-agents

## 摘要

Anthropic 的 long-running agent harness 文章指出，长任务 agent 的关键挑战是跨多个上下文窗口保持连续进展。文章用 initializer agent、coding agent、清洁工作状态和交接 artifact 改善跨 session 任务推进。

## 关键贡献

- Claude Agent SDK 是通用 harness，但 compaction 本身不足以解决长任务连续性。
- 初始环境搭建和每轮增量进展要拆成不同职责。
- 每个 session 结束时要留下清洁状态和可接续 artifact，让下一轮 agent 不必猜测历史。

## 对 AI 知识体系的归属

- 主归属：5. Agent 系统层
- 交叉链接：4. 上下文与知识层、6. 评估与可靠性层
- 作用：把 harness 连接到 context engineering、state handoff 和 long-running agent 可靠性。

## 关联

- [[concepts/AgentHarness与TraceEval]]
- [[concepts/上下文工程]]
- [[Research: Agent harness 与 trace eval]]

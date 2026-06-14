---
address: c-000204
type: source
title: "Scaling Managed Agents: Decoupling the brain from the hands"
source_url: https://www.anthropic.com/engineering/managed-agents
source_type: article
author: "Anthropic"
published: 2026-04-08
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - agents
  - orchestration
  - managed-agents
  - claude-code
status: active
related:
  - "[[concepts/AgentHarness与TraceEval]]"
  - "[[concepts/智能体优先工程]]"
---

# Scaling Managed Agents: Decoupling the brain from the hands

**来源**：Anthropic Engineering
**URL**：https://www.anthropic.com/engineering/managed-agents

## 摘要

Anthropic 介绍 Managed Agents 的接口设计：把 brain / harness、hands / sandbox、session log 解耦，使长任务 agent 能可靠恢复、扩展、隔离权限，并让 harness 随模型能力变化而替换。

## 关键贡献

- Session 是持久事件日志，不等于模型上下文窗口；harness 可以按需把事件切片转成上下文。
- Harness 离开 sandbox 后，sandbox 成为可替换工具，失败可被捕获并重试。
- 安全边界通过 token vault、MCP proxy 和 sandbox 隔离实现，避免 agent 直接接触凭据。

## 对 AI 知识体系的归属

- 主归属：5. Agent 系统层
- 交叉链接：6. 评估与可靠性层、7. 产品与组织层
- 作用：说明 harness、session、sandbox 是可分离的运行时接口。

## 关联

- [[concepts/AgentHarness与TraceEval]]
- [[concepts/智能体优先工程]]
- [[Research: Agent harness 与 trace eval]]

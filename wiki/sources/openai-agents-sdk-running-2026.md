---
address: c-000202
type: source
title: "Running agents - OpenAI Agents SDK"
source_url: https://openai.github.io/openai-agents-python/running_agents/
source_type: documentation
author: "OpenAI"
published: 2026-05-30
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - agents
  - runner
  - harness
status: active
related:
  - "[[concepts/AgentHarness与TraceEval]]"
  - "[[concepts/Loop机制]]"
---

# Running agents - OpenAI Agents SDK

**来源**：OpenAI Agents SDK documentation
**URL**：https://openai.github.io/openai-agents-python/running_agents/

## 摘要

该文档描述 OpenAI Agents SDK 如何运行 agent：runner 管理 agent loop，直到生成最终输出、触发 handoff 或达到最大回合数。

## 关键贡献

- Runner 是 harness 的核心执行器：它在模型生成、工具调用、handoff 和停止条件之间循环。
- `max_turns` 等限制把开放式 agent 行为约束在可控边界内。
- Run result 保存最终输出、输入历史、raw responses 和 last agent 等运行结果。

## 对 AI 知识体系的归属

- 主归属：5. Agent 系统层
- 交叉链接：6. 评估与可靠性层
- 作用：定义 agent harness 的执行模型，而不是只定义 prompt。

## 关联

- [[concepts/AgentHarness与TraceEval]]
- [[concepts/Loop机制]]
- [[Research: Agent harness 与 trace eval]]

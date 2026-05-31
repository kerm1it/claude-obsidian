---
address: c-000201
type: source
title: "Tracing - OpenAI Agents SDK"
source_url: https://openai.github.io/openai-agents-python/tracing/
source_type: documentation
author: "OpenAI"
published: 2026-05-30
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - agents
  - tracing
  - observability
status: active
related:
  - "[[concepts/AgentHarness与TraceEval]]"
  - "[[concepts/Agent评估体系]]"
---

# Tracing - OpenAI Agents SDK

**来源**：OpenAI Agents SDK documentation
**URL**：https://openai.github.io/openai-agents-python/tracing/

## 摘要

OpenAI Agents SDK 的 tracing 文档说明 SDK 会自动记录 agent run 中的关键事件，并把 trace / span 作为观测、调试和评估的基础。

## 关键贡献

- Trace 表示一个端到端工作流；span 表示其中的具体操作。
- 内置 span 类型包括 agent、generation、function、handoff、guardrail、response、custom。
- Tracing 默认开启，可通过 processor/exporter 接入外部观测系统。

## 对 AI 知识体系的归属

- 主归属：5. Agent 系统层
- 交叉链接：6. 评估与可靠性层
- 作用：让 harness 的执行过程成为可审计、可调试、可评分的证据。

## 关联

- [[concepts/AgentHarness与TraceEval]]
- [[concepts/Agent评估体系]]
- [[Research: Agent harness 与 trace eval]]

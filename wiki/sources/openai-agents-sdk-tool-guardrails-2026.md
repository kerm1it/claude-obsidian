---
address: c-000326
type: source
title: "Guardrails - OpenAI Agents SDK"
source_url: https://openai.github.io/openai-agents-js/guides/guardrails
source_type: documentation
author: "OpenAI"
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - ai
  - openai
  - agents
  - guardrails
status: active
related:
  - "[[concepts/ToolRiskPermissioning边界]]"
  - "[[concepts/AgentHarness与TraceEval]]"
---

# Guardrails - OpenAI Agents SDK

**来源**：OpenAI Agents SDK
**URL**：https://openai.github.io/openai-agents-js/guides/guardrails

## 摘要

OpenAI Agents SDK guardrails 文档说明 input、output 和 tool guardrails。Tool guardrails 可以在 function tool 调用前后验证或拒绝工具执行，是 agent runtime 动作准入的实现原语。

## 关键贡献

- 区分 agent-level input/output guardrails 与 per-tool guardrails。
- Tool guardrails 在工具执行前后运行，可 allow、reject 或 throw tripwire。
- 对本 vault 的意义：tool risk 不能只在最终答案过滤；高风险动作要在 tool-call boundary 上拦截。

## 对 AI 知识体系的归属

- 主归属：5. Agent 系统层
- 交叉链接：6. 评估与可靠性层

## 关联

- [[concepts/ToolRiskPermissioning边界]]
- [[Research: Tool risk permissioning 边界]]

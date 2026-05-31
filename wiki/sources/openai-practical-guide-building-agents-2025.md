---
address: c-000284
type: source
title: "A practical guide to building agents"
source_url: https://cdn.openai.com/business-guides-and-resources/a-practical-guide-to-building-agents.pdf
source_type: guide
author: "OpenAI"
published: "2025"
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - agents
  - guardrails
  - workflow-automation
status: active
related:
  - "[[concepts/ProductOrganizationLayer边界]]"
  - "[[concepts/AgentHarness与TraceEval]]"
  - "[[concepts/ReasoningEvalVerifier边界]]"
---

# A practical guide to building agents

**来源**：OpenAI PDF
**URL**：https://cdn.openai.com/business-guides-and-resources/a-practical-guide-to-building-agents.pdf

## 摘要

OpenAI 的 agent 构建指南把 agent 描述为能处理歧义、跨工具行动、执行多步骤任务的工作流自动化系统。指南强调从单 agent 和清晰工具开始，必要时再扩展多 agent，并在生产中加入 guardrails、风险分级和人工接管。

## 关键贡献

- Agent 适合复杂决策、非结构化数据、脆弱规则系统和端到端 workflow automation。
- 单 agent 能处理很多任务；只有工具清晰度、职责边界或维护性证明需要时，才拆成多 agent。
- Guardrails 是分层防御：输入过滤、relevance/safety classifier、工具风险分级、人工介入。
- 高风险动作应触发人工监督，直到系统可靠性被证据证明。
- 成功部署不是一次性全自动化，而是小范围验证、真实用户反馈、能力逐步增长。

## 对 AI 知识体系的归属

- 主归属：5. Agent 系统层
- 交叉链接：6. 评估与可靠性层、7. 产品与组织层
- 第 7 层启发：产品化 agent 必须把风险、人工接管、真实用户验证和业务价值纳入设计。

## 关联

- [[concepts/ProductOrganizationLayer边界]]
- [[concepts/AgentHarness与TraceEval]]
- [[Research: Product organization layer 边界]]

---
address: c-000285
type: source
title: "Agents SDK"
source_url: https://developers.openai.com/api/docs/guides/agents
source_type: documentation
author: "OpenAI"
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - agents-sdk
  - orchestration
  - observability
status: active
related:
  - "[[concepts/ProductOrganizationLayer边界]]"
  - "[[concepts/AgentHarness与TraceEval]]"
  - "[[sources/openai-agents-sdk-evolution-2026]]"
---

# Agents SDK

**来源**：OpenAI Docs
**URL**：https://developers.openai.com/api/docs/guides/agents

## 摘要

OpenAI Agents SDK 文档把 agent 定义为能计划、调用工具、跨专家协作，并保持足够状态来完成多步骤工作的应用。SDK 路径适合由应用服务器掌握 orchestration、tool execution、state、approvals 和 runtime behavior 的产品。

## 关键贡献

- Code-first agent app 需要应用拥有工具、MCP server、runtime behavior、storage 和 conversation strategy。
- 文档阅读路径从 quickstart 到 agent definitions、running agents、orchestration、guardrails/human review、results/state 和 observability。
- Agent Builder / ChatKit 是托管工作流和产品表面路径；SDK 是产品自己掌握运行时和审批的路径。
- 这说明第 5 层 harness 与第 7 层产品基础设施在工程上不可分割：上线 agent 必须同时设计状态、审批、trace 和 observability。

## 对 AI 知识体系的归属

- 主归属：5. Agent 系统层
- 交叉链接：6. 评估与可靠性层、7. 产品与组织层
- 第 7 层启发：当产品拥有 orchestration 和 approvals，就必须同时拥有组织责任、监控和用户体验。

## 关联

- [[concepts/ProductOrganizationLayer边界]]
- [[concepts/AgentHarness与TraceEval]]
- [[sources/openai-agents-sdk-evolution-2026]]

---
address: c-000283
type: source
title: "Building effective agents"
source_url: https://www.anthropic.com/engineering/building-effective-agents
source_type: engineering-blog
author: "Anthropic"
published: 2024-12-19
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - agents
  - workflows
  - product-engineering
status: active
related:
  - "[[concepts/ProductOrganizationLayer边界]]"
  - "[[concepts/AgentHarness与TraceEval]]"
  - "[[domains/AI知识体系]]"
---

# Building effective agents

**来源**：Anthropic Engineering
**URL**：https://www.anthropic.com/engineering/building-effective-agents
**发布时间**：2024-12-19

## 摘要

Anthropic 将 agentic systems 区分为 workflows 和 agents：workflow 走预定义路径，agent 根据环境反馈自主决定行动。这个区别对第 7 层很关键，因为产品化 AI 时，默认应先把高价值、可评估、可控的工作流做稳，再把开放式任务交给更自治的 agent。

## 关键贡献

- Workflows 适合路径清晰、可拆分、可控制的任务；agents 适合开放式、需要根据反馈持续调整的任务。
- 有效 agent 系统应从简单模式开始，只有复杂度被任务价值证明时才扩展。
- 工具设计是 agent 成功的关键工程面。Anthropic 在 SWE-bench agent 上花大量时间优化工具接口，而不只是调 prompt。
- Tool / workflow / agent 的边界帮助第 7 层判断：一个能力应该做成固定流程、辅助工具、还是自治 agent。

## 对 AI 知识体系的归属

- 主归属：5. Agent 系统层
- 交叉链接：7. 产品与组织层、6. 评估与可靠性层
- 第 7 层启发：产品化时从 workflow fit 和可评估性开始，而不是从“多 agent 架构”开始。

## 关联

- [[concepts/ProductOrganizationLayer边界]]
- [[concepts/AgentHarness与TraceEval]]
- [[Research: Product organization layer 边界]]

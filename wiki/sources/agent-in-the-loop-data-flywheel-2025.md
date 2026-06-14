---
address: c-000311
type: source
title: "Agent-in-the-Loop Data Flywheel"
source_url: https://arxiv.org/abs/2507.14225
source_type: paper
author: "Yao et al."
published: 2025-07-18
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - data-flywheel
  - agents
  - customer-support
status: active
related:
  - "[[concepts/DataFlywheelFeedbackLoop边界]]"
  - "[[concepts/AgentHarness与TraceEval]]"
---

# Agent-in-the-Loop Data Flywheel

**来源**：arXiv
**URL**：https://arxiv.org/abs/2507.14225

## 摘要

这项研究以客户支持为场景，提出 agent-in-the-loop data flywheel：用 agent routing、judge LLM、人工反馈和持续数据生成，让 LLM 在生产任务中持续改进。

## 关键贡献

- 将真实服务场景、人工反馈和 LLM-as-judge 组合成数据飞轮。
- 不同任务可被路由到不同处理路径，以提高数据和训练信号质量。
- 研究显示生产反馈需要任务分层、质量判断和训练数据生成，而不是无差别回灌。
- 对本 vault 的意义：agent trace 是第 7 层数据飞轮的重要上游，但必须经第 6 层评估。

## 对 AI 知识体系的归属

- 主归属：7. 产品与组织层
- 交叉链接：5. Agent 系统层、6. 评估与可靠性层

## 关联

- [[concepts/DataFlywheelFeedbackLoop边界]]
- [[Research: Data flywheel feedback loop 边界]]

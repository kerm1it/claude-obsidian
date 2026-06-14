---
address: c-000458
type: source
title: "Evaluation-Driven Development and Operations of LLM Agents"
source_url: https://arxiv.org/abs/2411.13768
source_type: paper
author: "Boming Xia, Qinghua Lu, Liming Zhu, Zhenchang Xing, Dehai Zhao, Hao Zhang"
published: 2025-11-17
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: medium
tags:
  - ai-agents
  - evals
  - eddops
  - llmops
status: active
related:
  - "[[concepts/OfflineOnlineEvalCorrelation边界]]"
  - "[[concepts/AgentHarness与TraceEval]]"
---

# Evaluation-Driven Development and Operations of LLM Agents

**来源**：arXiv
**URL**：https://arxiv.org/abs/2411.13768
**版本**：2025-11-17 修订版

## 摘要

这篇论文提出 EDDOps：把 LLM agent 的 offline development-time evaluation 和 online runtime evaluation 统一到闭环中，使 evaluation evidence 同时驱动 runtime adaptation 和 governed redevelopment。

## 关键贡献

- 说明传统固定 benchmark 和静态测试套件不足以覆盖开放、概率性、会部署后适应的 agent 行为。
- 把 evaluation 作为生命周期中的持续治理功能，而不是最终 checkpoint。
- 对本 vault 的意义：offline/online eval correlation 是 agent EDDOps 的质量校准环节。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：5. Agent 系统层、7. 产品与组织层、8. 自我改进与前沿层

## 关联

- [[concepts/OfflineOnlineEvalCorrelation边界]]
- [[Research: Offline online eval correlation 边界]]

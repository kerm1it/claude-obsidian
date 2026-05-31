---
address: c-000445
type: source
title: "Expanding the AI Evaluation Toolbox with Statistical Models"
source_url: https://www.nist.gov/publications/expanding-ai-evaluation-toolbox-statistical-models
source_type: report
author: "Andrew Keller, Kweku Kwegyir-Aggrey, Ryan Steed, Anita Rao, Julia Sharp, Amanda Bergman"
published: 2026-02-17
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - ai
  - evals
  - statistics
  - benchmarks
status: active
related:
  - "[[concepts/EvalUncertaintyCommunicationReleaseCard边界]]"
  - "[[concepts/EvalResultInterpretationDecisionThreshold边界]]"
  - "[[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]"
---

# Expanding the AI Evaluation Toolbox with Statistical Models

**来源**：NIST
**URL**：https://www.nist.gov/publications/expanding-ai-evaluation-toolbox-statistical-models
**发布**：2026-02-17

## 摘要

NIST 这份报告讨论 AI benchmark 统计建模。它指出一些 benchmark 指标计算方式会产生无效 uncertainty estimates 或隐含未识别的评估假设，并区分固定 benchmark 上的 performance 与对相似潜在题目集合的 generalized accuracy。

## 关键贡献

- 把 benchmark accuracy 与 generalized accuracy 区分开，避免把固定题集分数过度外推。
- 使用 generalized linear mixed models 估计 frontier LLM 在多个 benchmark 上的 generalized accuracy 和 uncertainty。
- 对本 vault 的意义：release card 需要说明分数能外推到什么范围，不能把 benchmark 点估计直接写成产品质量事实。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层

## 关联

- [[concepts/EvalUncertaintyCommunicationReleaseCard边界]]
- [[Research: Eval uncertainty communication release card 边界]]

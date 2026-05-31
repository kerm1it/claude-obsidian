---
address: c-000425
type: source
title: "BetterBench: Assessing AI Benchmarks, Uncovering Issues, and Establishing Best Practices"
source_url: https://arxiv.org/abs/2411.12990
source_type: paper
author: "Anka Reuel, Amelia Hardy, Chandler Smith, Max Lamparth, Malcolm Hardy, Mykel J. Kochenderfer"
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - benchmarks
  - evals
  - statistical-significance
status: active
related:
  - "[[concepts/EvalUncertaintyCommunicationReleaseCard边界]]"
  - "[[concepts/EvalResultInterpretationDecisionThreshold边界]]"
  - "[[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]"
---

# BetterBench: Assessing AI Benchmarks, Uncovering Issues, and Establishing Best Practices

**来源**：arXiv / NeurIPS 2024 Datasets and Benchmarks
**URL**：https://arxiv.org/abs/2411.12990

## 摘要

BetterBench 提出 46 项 benchmark 生命周期最佳实践，并评估 24 个 AI benchmarks。论文指出常用 benchmark 在质量、可复现性、统计显著性和方差报告上存在明显差异。

## 关键贡献

- 将 statistical significance、variance bounds、replicability 和 benchmark lifecycle 纳入 benchmark 质量评估。
- 说明 benchmark 分数是否可用于模型选择或政策判断，取决于 benchmark 本身的设计和可复现性。
- 对本 vault 的意义：eval result interpretation 必须关注 uncertainty、variance 和 benchmark 质量，不能把单个分数直接当成质量事实。
- 对 release card 的意义：卡片需要报告 benchmark 质量和 uncertainty，不只报告 candidate 在 benchmark 上的排名。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层

## 关联

- [[concepts/EvalResultInterpretationDecisionThreshold边界]]
- [[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]
- [[concepts/EvalUncertaintyCommunicationReleaseCard边界]]

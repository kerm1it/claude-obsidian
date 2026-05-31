---
address: c-000453
type: source
title: "Do Offline Metrics Predict Online Performance in Recommender Systems?"
source_url: https://arxiv.org/abs/2011.07931
source_type: paper
author: "Karl Krauth, Sarah Dean, Alex Zhao, Wenshuo Guo, Mihaela Curmei, Benjamin Recht, Michael I. Jordan"
published: 2020-11-07
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - evals
  - recommender-systems
  - online-evaluation
  - offline-metrics
status: active
related:
  - "[[concepts/OfflineOnlineEvalCorrelation边界]]"
  - "[[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]"
---

# Do Offline Metrics Predict Online Performance in Recommender Systems?

**来源**：arXiv
**URL**：https://arxiv.org/abs/2011.07931
**发布**：2020-11-07

## 摘要

这篇论文研究 recommender systems 中 offline metrics 是否预测 online performance。作者在六个模拟环境中评估 11 个推荐器，发现 offline metrics 在一定范围内与 online performance 相关，但离线指标提升对线上表现存在递减回报，且候选排序依赖初始离线数据量。

## 关键贡献

- 明确把 offline metric → online performance 的相关性当作研究问题。
- 说明离线改善不等于线性线上收益，线上动态和用户反馈会改变效果。
- 对本 vault 的意义：LLM/agent eval 也需要持续验证离线质量门对生产 outcome 的预测能力。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层

## 关联

- [[concepts/OfflineOnlineEvalCorrelation边界]]
- [[Research: Offline online eval correlation 边界]]

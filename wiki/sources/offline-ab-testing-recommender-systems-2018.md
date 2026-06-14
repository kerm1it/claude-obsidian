---
address: c-000454
type: source
title: "Offline A/B testing for Recommender Systems"
source_url: https://arxiv.org/abs/1801.07030
source_type: paper
author: "Alexandre Gilotte, Clément Calauzènes, Thomas Nedelec, Alexandre Abraham, Simon Dollé"
published: 2018-01-22
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - evals
  - ab-testing
  - off-policy-evaluation
  - recommender-systems
status: active
related:
  - "[[concepts/OfflineOnlineEvalCorrelation边界]]"
  - "[[concepts/EvalResultInterpretationDecisionThreshold边界]]"
---

# Offline A/B testing for Recommender Systems

**来源**：arXiv / WSDM 2018
**URL**：https://arxiv.org/abs/1801.07030
**发布**：2018-01-22

## 摘要

这篇论文研究在上线 A/B testing 前，如何用历史数据和 counterfactual / off-policy estimators 估计新推荐策略可能带来的 revenue uplift，并用商业推荐系统中的线上 A/B business metrics 检验 estimator 相关性。

## 关键贡献

- 说明 offline A/B / OPE 的目标是减少昂贵线上实验中的坏策略，而不是替代所有线上实验。
- 把 estimator 的 bias-variance tradeoff 和线上 business metric correlation 作为评价标准。
- 对本 vault 的意义：LLM release gate 可以用离线 eval 筛选候选，但高影响变更仍需要 canary/A-B/online eval 校准。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层

## 关联

- [[concepts/OfflineOnlineEvalCorrelation边界]]
- [[Research: Offline online eval correlation 边界]]

---
address: c-000455
type: source
title: "How well do offline metrics predict online performance of product ranking models?"
source_url: https://www.amazon.science/publications/how-well-do-offline-metrics-predict-online-performance-of-product-ranking-models
source_type: paper
author: "Xiaojie Wang, Ruoyuan Gao, Anoop Jain, Graham Edge, Sachin Ahuja"
published: 2023
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - evals
  - product-ranking
  - offline-metrics
  - online-metrics
status: active
related:
  - "[[concepts/OfflineOnlineEvalCorrelation边界]]"
---

# How well do offline metrics predict online performance of product ranking models?

**来源**：Amazon Science
**URL**：https://www.amazon.science/publications/how-well-do-offline-metrics-predict-online-performance-of-product-ranking-models
**发布**：2023

## 摘要

Amazon Science 这篇 product ranking 论文研究 offline metrics 是否能预测 online performance，并用 directional agreement with the business metric 评估 offline metrics。

## 关键贡献

- 把 offline metric 和 online business metric 的同向性作为工业评估对象。
- 强调 ranking / recommender 这类产品系统不能只依赖离线分数。
- 对本 vault 的意义：AI release card 中的离线 eval delta 应在发布后与线上 outcome 做 directional agreement 复盘。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层

## 关联

- [[concepts/OfflineOnlineEvalCorrelation边界]]
- [[Research: Offline online eval correlation 边界]]

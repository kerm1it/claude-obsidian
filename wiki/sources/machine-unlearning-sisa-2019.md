---
address: c-000383
type: source
title: "Machine Unlearning"
source_url: https://arxiv.org/abs/1912.03817
source_type: paper
author: "Lucas Bourtoule et al."
date_published: 2019-12-09
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - machine-unlearning
  - privacy
  - data-deletion
status: active
related:
  - "[[concepts/DataDeletionUnlearningImpact边界]]"
---

# Machine Unlearning

**来源**：arXiv / IEEE S&P 2021
**URL**：https://arxiv.org/abs/1912.03817

## 摘要

这篇论文提出 SISA training，用 sharding、isolation、slicing、aggregation 限制单个数据点对模型参数的影响范围，并缓存中间训练结果，以降低未来删除请求触发的重训成本。

## 关键贡献

- 将用户删除请求和模型 memorization 风险连接到 ML 系统设计。
- 提出训练前就为未来 unlearning 设计模型和数据分区。
- 证明 unlearning 不是只删数据表，还可能要处理模型参数中的训练影响。

## 对 AI 知识体系的归属

- 主归属：2. 模型构建层
- 交叉链接：6. 评估与可靠性层、7. 产品与组织层

## 关联

- [[concepts/DataDeletionUnlearningImpact边界]]
- [[Research: Data deletion unlearning impact 边界]]

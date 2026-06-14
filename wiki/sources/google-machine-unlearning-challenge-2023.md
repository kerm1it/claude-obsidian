---
address: c-000384
type: source
title: "Announcing the first Machine Unlearning Challenge"
source_url: https://research.google/blog/announcing-the-first-machine-unlearning-challenge/
source_type: engineering-blog
author: "Google Research"
date_published: 2023-06-29
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - machine-unlearning
  - evals
  - privacy
status: active
related:
  - "[[concepts/DataDeletionUnlearningImpact边界]]"
---

# Announcing the first Machine Unlearning Challenge

**来源**：Google Research Blog
**URL**：https://research.google/blog/announcing-the-first-machine-unlearning-challenge/

## 摘要

Google Research 宣布 NeurIPS 2023 Machine Unlearning Challenge，目标是推动删除 forget set 影响且保持模型 utility 的算法和统一评估协议。

## 关键贡献

- 将 ideal unlearning 表述为接近“从未用 forget set 训练过”的模型。
- 强调 unlearning 有三重目标：forgetting quality、retained utility、efficiency。
- 指出领域中评估指标不统一，包括 unlearn samples accuracy、retrained-model distance、membership inference attacks 等。
- 对本 vault 的意义：删除/遗忘必须由第 6 层 eval 验证，不能只宣称“已删除”。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：2. 模型构建层、7. 产品与组织层

## 关联

- [[concepts/DataDeletionUnlearningImpact边界]]
- [[Research: Data deletion unlearning impact 边界]]

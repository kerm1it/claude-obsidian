---
address: c-000385
type: source
title: "Machine Unlearning: A Comprehensive Survey"
source_url: https://arxiv.org/abs/2405.07406
source_type: paper
author: "Weiqi Wang et al."
date_published: 2024-05-13
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: medium
tags:
  - machine-unlearning
  - survey
  - privacy
status: active
related:
  - "[[concepts/DataDeletionUnlearningImpact边界]]"
---

# Machine Unlearning: A Comprehensive Survey

**来源**：arXiv
**URL**：https://arxiv.org/abs/2405.07406

## 摘要

这篇综述系统整理 machine unlearning 的方法与问题，覆盖 centralized unlearning、exact unlearning、approximate unlearning、distributed/federated/graph unlearning、verification，以及 privacy/security risks。

## 关键贡献

- 将 machine unlearning 定义为从已训练模型中移除 erased subset 对训练结果的贡献。
- 区分 exact 与 approximate unlearning，以及 verification 和 privacy/security 议题。
- 对本 vault 的意义：unlearning 是一族方法和验证问题，不是单一算法；工程上必须绑定 lineage、eval 和 audit。

## 对 AI 知识体系的归属

- 主归属：2. 模型构建层
- 交叉链接：6. 评估与可靠性层、7. 产品与组织层

## 关联

- [[concepts/DataDeletionUnlearningImpact边界]]
- [[Research: Data deletion unlearning impact 边界]]

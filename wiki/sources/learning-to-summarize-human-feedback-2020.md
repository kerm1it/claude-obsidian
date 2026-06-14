---
address: c-000389
type: source
title: "Learning to summarize from human feedback"
source_url: https://arxiv.org/abs/2009.01325
source_type: paper
author: "Nisan Stiennon et al."
date_published: 2020-09-02
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - human-feedback
  - summarization
  - rlhf
status: active
related:
  - "[[concepts/HumanFeedbackAnnotationOps边界]]"
---

# Learning to summarize from human feedback

**来源**：arXiv / NeurIPS 2020
**URL**：https://arxiv.org/abs/2009.01325

## 摘要

这篇论文指出 summarization 的训练和评估常被 ROUGE 等代理指标限制，并通过收集人类 summary comparisons、训练 reward model、再优化 summarization policy 来提升人类偏好的摘要质量。

## 关键贡献

- 说明人类偏好数据可以修正自动指标与真实质量之间的错位。
- 将 high-quality human comparisons、reward model 和 policy optimization 组合成可复用流程。
- 对本 vault 的意义：annotation ops 必须把“人真正关心什么”写进 rubric 和 preference 数据，而不是只优化容易计算的代理指标。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：2. 模型构建层、6. reward hacking / eval overfitting

## 关联

- [[concepts/HumanFeedbackAnnotationOps边界]]
- [[Research: Human feedback annotation ops 边界]]

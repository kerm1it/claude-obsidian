---
address: c-000390
type: source
title: "Training a Helpful and Harmless Assistant with Reinforcement Learning from Human Feedback"
source_url: https://arxiv.org/abs/2204.05862
source_type: paper
author: "Bai et al."
date_published: 2022-04-12
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - rlhf
  - human-feedback
  - alignment
status: active
related:
  - "[[concepts/HumanFeedbackAnnotationOps边界]]"
---

# Training a Helpful and Harmless Assistant with Reinforcement Learning from Human Feedback

**来源**：arXiv
**URL**：https://arxiv.org/abs/2204.05862

## 摘要

这篇 Anthropic 论文用 RLHF 训练 assistant 的 helpfulness 和 harmlessness。它展示了偏好数据不只用于“答案更好”，也用于塑造安全、无害和行为边界。

## 关键贡献

- 将 helpfulness 与 harmlessness 作为可收集、可建模、可优化的人类偏好维度。
- 说明 annotation ops 要处理价值冲突、风险偏好和政策边界，而不仅是事实正确性。
- 对本 vault 的意义：human feedback 数据进入模型构建前必须有 rubric、分歧处理和安全质量门。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：2. 模型构建层、7. 产品与组织层

## 关联

- [[concepts/HumanFeedbackAnnotationOps边界]]
- [[Research: Human feedback annotation ops 边界]]

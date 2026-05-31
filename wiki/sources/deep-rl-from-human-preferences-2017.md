---
address: c-000388
type: source
title: "Deep reinforcement learning from human preferences"
source_url: https://arxiv.org/abs/1706.03741
source_type: paper
author: "Paul Christiano et al."
date_published: 2017-06-12
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - human-feedback
  - rlhf
  - preferences
status: active
related:
  - "[[concepts/HumanFeedbackAnnotationOps边界]]"
---

# Deep reinforcement learning from human preferences

**来源**：arXiv
**URL**：https://arxiv.org/abs/1706.03741

## 摘要

这篇论文用人类对 trajectory segment 的 pairwise preference 来训练 reward model，再用 reward model 训练 RL agent。论文显示，在没有手写 reward function 的复杂任务中，少量人类比较反馈可以产生有用行为。

## 关键贡献

- 将人类偏好比较固定为可训练 reward signal，而不是只依赖人工写 reward。
- 证明 human feedback 可以在反馈量较少时驱动复杂行为学习。
- 对本 vault 的意义：human feedback / annotation ops 的基础单位之一是 pairwise comparison，而不是“给答案打一个分”。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：2. 模型构建层、8. 自我改进与前沿层

## 关联

- [[concepts/HumanFeedbackAnnotationOps边界]]
- [[Research: Human feedback annotation ops 边界]]

---
address: c-000175
type: source
title: "Training language models to follow instructions with human feedback"
source_url: https://arxiv.org/abs/2203.02155
source_type: paper
author: "Ouyang et al."
published: 2022
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - rlhf
  - instruction-tuning
  - paper
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/HumanFeedbackAnnotationOps边界]]"
---

# Training language models to follow instructions with human feedback

**来源**：arXiv:2203.02155
**作者**：Long Ouyang 等
**发布时间**：2022

## 摘要

InstructGPT 论文说明：更大的语言模型不天然更符合用户意图。通过示范数据监督微调，再用人类偏好排序训练奖励模型并进行 RLHF，可以让模型更有帮助、更真实、更少毒性。

## 关键贡献

- 把“基础模型”转化为“指令跟随模型”的经典流程：SFT → preference data → reward model → RLHF。
- 说明模型构建不只是预训练，还包括行为塑形和对齐。
- 论文中 1.3B InstructGPT 在人类偏好上超过 175B GPT-3，证明“构建方式”能改变产品可用性。
- 对本 vault 的意义：人工示范和输出排序不是附属劳动，而是第 6 层 human feedback / annotation ops 生产的训练证据。

## 对 AI 知识体系的归属

- 主归属：2. 模型构建层
- 上游：1. 基础理论层、预训练模型
- 下游：3. 推理与能力层、7. 产品与组织层

## 关联

- [[domains/AI知识体系]]
- [[Research: AI知识体系总览]]
- [[concepts/HumanFeedbackAnnotationOps边界]]
- [[Research: Human feedback annotation ops 边界]]

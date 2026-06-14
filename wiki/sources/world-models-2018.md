---
address: c-000242
type: source
title: "World Models"
source_url: https://arxiv.org/abs/1803.10122
source_type: paper
author: "David Ha, Jürgen Schmidhuber"
published: 2018-05-09
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - world-model
  - reinforcement-learning
status: active
related:
  - "[[concepts/多模态与世界模型边界]]"
---

# World Models

**来源**：arXiv:1803.10122
**URL**：https://arxiv.org/abs/1803.10122

## 摘要

Ha 和 Schmidhuber 的 World Models 是世界模型概念的经典来源之一：用无监督方式学习环境的压缩空间和时间表示，再用这个模型特征训练 agent policy。

## 关键贡献

- 世界模型不是视频逼真度，而是环境状态和时间动态的可用表示。
- Agent 可以在 world model 生成的 hallucinated dream 中训练 policy。
- 世界模型直接连接第 3 层能力和第 5 层 agent 学习。

## 对 AI 知识体系的归属

- 主归属：3. 推理与能力层
- 交叉链接：5. Agent 系统层、8. 自我改进与前沿层
- 作用：提供 world model 的稳定基础定义。

## 关联

- [[concepts/多模态与世界模型边界]]
- [[Research: 多模态与世界模型边界]]

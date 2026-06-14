---
address: c-000301
type: source
title: "Scaling laws for reward model overoptimization"
source_url: https://openai.com/blog/scaling-laws-for-reward-model-overoptimization/
source_type: research-blog
author: "Leo Gao, John Schulman, Jacob Hilton"
published: 2022-10-19
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - reward-models
  - goodhart-law
  - rlhf
status: active
related:
  - "[[concepts/RewardHackingEvalOverfitting边界]]"
  - "[[concepts/ReasoningEvalVerifier边界]]"
---

# Scaling laws for reward model overoptimization

**来源**：OpenAI Research
**URL**：https://openai.com/blog/scaling-laws-for-reward-model-overoptimization/
**发布时间**：2022-10-19

## 摘要

这项研究刻画 reward model overoptimization：reward model 是人类偏好的不完美代理，过度优化会让代理分数升高而真实偏好表现下降。这是 Goodhart 定律在 RLHF / reward model 场景中的直接表现。

## 关键贡献

- Learned reward model 不是可靠真值，而是可被优化压力利用的代理。
- 优化强度、reward model 大小和数据量会影响 overoptimization 发生的点。
- 更多 reward model 数据可以推迟过度优化，但不能取消代理目标和真实目标之间的结构性差距。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：2. 模型构建层
- 作用：解释为什么 reward model / verifier 也必须有独立 hold-out eval。

## 关联

- [[concepts/RewardHackingEvalOverfitting边界]]
- [[concepts/ReasoningEvalVerifier边界]]

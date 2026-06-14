---
address: c-000267
type: source
title: "RewardBench: Evaluating Reward Models for Language Modeling"
source_url: https://arxiv.org/abs/2403.13787
source_type: paper
author: "Nathan Lambert et al."
published: 2024-03-20
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - reward-models
  - evals
  - rlhf
status: active
related:
  - "[[concepts/ReasoningEvalVerifier边界]]"
  - "[[concepts/RewardHackingEvalOverfitting边界]]"
sources:
  - "https://github.com/allenai/reward-bench"
---

# RewardBench: Evaluating Reward Models for Language Modeling

**来源**：arXiv / AllenAI
**URL**：https://arxiv.org/abs/2403.13787

## 摘要

RewardBench 是用于评估 reward models 的 benchmark 和代码库。它用 prompt-chosen-rejected 三元组覆盖 chat、reasoning、safety 和分布外查询，帮助分析 reward model 的偏好和失败模式。

## 关键贡献

- 把 reward model 本身作为待评估对象，而不是默认可信评分器。
- 覆盖 subtle but verifiable 的 preference cases，例如 bug、错误事实和安全拒答。
- 比较 classifier RM、DPO implicit reward model 和 generative judge 等不同模式。
- 揭示 reward models 在拒答倾向、推理和 instruction following 上的限制。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：2. 模型构建层
- 作用：说明 verifier/reward model 也需要独立 eval 和回归套件。

## 关联

- [[concepts/ReasoningEvalVerifier边界]]
- [[concepts/RewardHackingEvalOverfitting边界]]
- [[Research: Reasoning eval verifier 边界]]

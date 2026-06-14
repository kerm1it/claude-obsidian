---
address: c-000423
type: source
title: "Chatbot Arena: An Open Platform for Evaluating LLMs by Human Preference"
source_url: https://arxiv.org/abs/2403.04132
source_type: paper
author: "Wei-Lin Chiang et al."
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - llm-evaluation
  - human-preference
  - confidence-intervals
status: active
related:
  - "[[concepts/EvalResultInterpretationDecisionThreshold边界]]"
  - "[[concepts/LLMJudgeAIFeedbackCalibration边界]]"
---

# Chatbot Arena: An Open Platform for Evaluating LLMs by Human Preference

**来源**：arXiv
**URL**：https://arxiv.org/abs/2403.04132
**发布**：2024-03-07

## 摘要

Chatbot Arena 使用 crowdsourced pairwise human preference 来评估 LLM，并用统计方法把成对偏好转成模型排名。论文强调多样化用户问题、人类偏好一致性和排名不确定性。

## 关键贡献

- 使用 pairwise comparison 和 Bradley-Terry / Elo-style rating 表示模型偏好排名。
- 通过人类投票和统计估计支撑 LLM 排行榜，而不是单一静态 benchmark。
- 对本 vault 的意义：LLM eval 结果应表达不确定性；排名相邻或 confidence interval 重叠时，不应把榜单顺序当成确定差异。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层

## 关联

- [[concepts/EvalResultInterpretationDecisionThreshold边界]]
- [[concepts/LLMJudgeAIFeedbackCalibration边界]]

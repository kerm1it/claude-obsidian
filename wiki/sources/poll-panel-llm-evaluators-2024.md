---
address: c-000414
type: source
title: "Replacing Judges with Juries: Evaluating LLM Generations with a Panel of Diverse Models"
source_url: https://arxiv.org/abs/2404.18796
source_type: paper
author: "Pat Verga et al."
published: 2024-04-29
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - ai
  - evals
  - llm-as-judge
  - panel
status: active
related:
  - "[[concepts/LLMJudgeAIFeedbackCalibration边界]]"
  - "[[concepts/JudgeDriftGraderObservability边界]]"
---

# Replacing Judges with Juries: Evaluating LLM Generations with a Panel of Diverse Models

**来源**：arXiv
**URL**：https://arxiv.org/abs/2404.18796
**发布时间**：2024-04-29

## 摘要

论文提出 Panel of LLM evaluators (PoLL)，用多个较小且多样的 judge 模型替代单一大型 judge。作者在多个 judge settings 和 datasets 中发现 PoLL 可降低单一模型偏差，并显著降低成本。

## 关键贡献

- 单一强 judge 不是唯一选择；jury / panel 是降低偏差和成本的工程策略。
- diverse model families 可降低 intra-model bias，但不自动保证独立。
- panel 输出仍需 human anchor、bias suite 和 disagreement handling。
- 对本 vault 的意义：multi-judge consensus 是 LLM judge calibration 的一种 mitigation，不是免校准。
- 对 grader observability 的意义：panel 需要监控 inter-judge disagreement 和 correlated drift，不能把投票当作永久稳定真相。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层

## 关联

- [[concepts/LLMJudgeAIFeedbackCalibration边界]]
- [[concepts/JudgeDriftGraderObservability边界]]
- [[Research: LLM-as-judge AI feedback calibration 边界]]

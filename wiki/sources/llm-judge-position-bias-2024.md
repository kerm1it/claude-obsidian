---
address: c-000412
type: source
title: "Judging the Judges: A Systematic Study of Position Bias in LLM-as-a-Judge"
source_url: https://arxiv.org/abs/2406.07791
source_type: paper
author: "Lin Shi et al."
published: 2024-06-12
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - ai
  - evals
  - llm-as-judge
  - bias
status: active
related:
  - "[[concepts/LLMJudgeAIFeedbackCalibration边界]]"
  - "[[concepts/JudgeDriftGraderObservability边界]]"
  - "[[concepts/RewardHackingEvalOverfitting边界]]"
---

# Judging the Judges: A Systematic Study of Position Bias in LLM-as-a-Judge

**来源**：arXiv
**URL**：https://arxiv.org/abs/2406.07791
**发布时间**：2024-06-12

## 摘要

论文系统研究 LLM judge 在 pairwise 和 listwise comparison 中的 position bias，提出 repetition stability、position consistency 和 preference fairness 三个指标，并在 MTBench 和 DevBench 上分析 judge、candidate 和 task 因素。

## 关键贡献

- 明确 position bias 不是随机噪声，而是 judge 可靠性风险。
- 给出可工程化的 judge bias 指标。
- 说明答案质量差距、任务类型和 judge 模型都会影响偏差。
- 对本 vault 的意义：pairwise judge 必须做 order swap、position consistency 和 human calibration。
- 在 grader observability 中，position swap delta 应成为持续监控信号，而不是一次性论文检查。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：6. reward hacking / eval overfitting

## 关联

- [[concepts/LLMJudgeAIFeedbackCalibration边界]]
- [[concepts/JudgeDriftGraderObservability边界]]
- [[Research: LLM-as-judge AI feedback calibration 边界]]

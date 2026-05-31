---
address: c-000432
type: source
title: "Judge's Verdict: A Comprehensive Analysis of LLM Judge Capability Through Human Agreement"
source_url: https://arxiv.org/abs/2510.09738
source_type: paper
author: "Steve Han et al."
published: 2025-10-10
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - ai
  - evals
  - llm-as-judge
  - human-agreement
status: active
related:
  - "[[concepts/JudgeDriftGraderObservability边界]]"
  - "[[concepts/LLMJudgeAIFeedbackCalibration边界]]"
---

# Judge's Verdict

**来源**：arXiv
**URL**：https://arxiv.org/abs/2510.09738
**发布时间**：2025-10-10

## 摘要

论文分析 LLM judge 与人类判断的一致性，强调不能只用 correlation 判断模型裁判是否可用。作者提出两阶段分析：先看 LLM 与 human mean 的相关性，再用 Cohen's Kappa 分析一致性。

## 关键贡献

- 把 LLM judge 评估从“分数相关”推进到“人类一致性和可靠性”。
- 发现不同 LLM judge 在不同任务上的 human-like / super-consistent 行为不同。
- 对本 vault 的意义：grader observability 需要持续跟踪 human agreement、kappa、分布和任务 slice，而不是只看单次总体相关。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：LLM judge calibration、judge drift、eval threshold

## 关联

- [[concepts/JudgeDriftGraderObservability边界]]
- [[concepts/LLMJudgeAIFeedbackCalibration边界]]
- [[Research: Judge drift grader observability 边界]]

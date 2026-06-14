---
address: c-000415
type: source
title: "LLM Evaluators Recognize and Favor Their Own Generations"
source_url: https://arxiv.org/abs/2404.13076
source_type: paper
author: "Arjun Panickssery, Samuel R. Bowman, Shi Feng"
published: 2024-04-15
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - ai
  - evals
  - self-preference
  - llm-as-judge
status: active
related:
  - "[[concepts/LLMJudgeAIFeedbackCalibration边界]]"
  - "[[concepts/JudgeDriftGraderObservability边界]]"
  - "[[concepts/RewardHackingEvalOverfitting边界]]"
---

# LLM Evaluators Recognize and Favor Their Own Generations

**来源**：arXiv
**URL**：https://arxiv.org/abs/2404.13076
**发布时间**：2024-04-15

## 摘要

论文研究 LLM evaluator 在评分自己生成的文本时的 self-preference bias。作者发现 LLM 能以非平凡准确率识别自己的输出，并且 self-recognition 与 self-preference 强度相关。

## 关键贡献

- 同一模型或同源模型同时当 evaluator 和 evaluatee，会造成系统性偏差。
- self-preference 不只影响 benchmark，也影响 reward modeling、constitutional AI 和 self-refinement。
- 对本 vault 的意义：AI feedback 进入训练和自我改进前，必须做 cross-family、blind identity 和 human gold 校准。
- 在长期 grader observability 中，self-preference lift 应作为候选模型家族变化时的漂移信号。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：8. 自我改进与前沿层

## 关联

- [[concepts/LLMJudgeAIFeedbackCalibration边界]]
- [[concepts/JudgeDriftGraderObservability边界]]
- [[Research: LLM-as-judge AI feedback calibration 边界]]

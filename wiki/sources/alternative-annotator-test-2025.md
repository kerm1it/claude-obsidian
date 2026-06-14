---
address: c-000416
type: source
title: "The Alternative Annotator Test for LLM-as-a-Judge"
source_url: https://arxiv.org/abs/2501.10970
source_type: paper
author: "Nitay Calderon, Roi Reichart, Rotem Dror"
published: 2025-01-19
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - ai
  - evals
  - llm-as-judge
  - annotation
status: active
related:
  - "[[concepts/LLMJudgeAIFeedbackCalibration边界]]"
  - "[[concepts/JudgeDriftGraderObservability边界]]"
  - "[[concepts/HumanFeedbackAnnotationOps边界]]"
---

# The Alternative Annotator Test for LLM-as-a-Judge

**来源**：arXiv
**URL**：https://arxiv.org/abs/2501.10970
**发布时间**：2025-01-19

## 摘要

论文提出 Alternative Annotator Test，用统计程序判断 LLM annotator / judge 是否能替代人类标注，并引入可解释的 annotator 比较指标。实验覆盖语言和视觉语言任务、多个 LLM 与多种 prompting 技术。

## 关键贡献

- 把“能不能用 LLM 替代人类标注”从经验判断变成统计检验问题。
- 只需要 modest human-annotated subset，就能对 LLM annotator 做替代判断。
- 提醒 prompting 技术会显著影响 judge quality。
- 对本 vault 的意义：AI feedback calibration 要有 human anchor 和统计替代门，而不是直接用 LLM 标签替代人工。
- 对 grader observability 的意义：上线后的 LLM annotator 仍要定期用 modest human-annotated subset 复测替代资格。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：human feedback、data quality

## 关联

- [[concepts/LLMJudgeAIFeedbackCalibration边界]]
- [[concepts/JudgeDriftGraderObservability边界]]
- [[Research: LLM-as-judge AI feedback calibration 边界]]

---
address: c-000413
type: source
title: "Judging the Judges: Evaluating Alignment and Vulnerabilities in LLMs-as-Judges"
source_url: https://arxiv.org/abs/2406.12624
source_type: paper
author: "Aman Singh Thakur et al."
published: 2024-06-18
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - ai
  - evals
  - llm-as-judge
  - calibration
status: active
related:
  - "[[concepts/LLMJudgeAIFeedbackCalibration边界]]"
  - "[[concepts/JudgeDriftGraderObservability边界]]"
---

# Judging the Judges: Evaluating Alignment and Vulnerabilities in LLMs-as-Judges

**来源**：arXiv
**URL**：https://arxiv.org/abs/2406.12624
**发布时间**：2024-06-18

## 摘要

论文在 inter-human agreement 较高的干净设置中研究 13 个 LLM judge。结论是强 judge 可达到一定 human alignment，但仍落后于人类之间一致性，并存在 prompt complexity、prompt length、leniency bias 和评分差异。

## 关键贡献

- simple percent agreement 不够，应使用 Cohen's kappa 等更严格的 alignment 指标。
- judge 排名模型的信号和 judge 与 human 打分一致性是不同问题。
- prompt sensitivity 与 leniency bias 会影响 judge 可用性。
- 对本 vault 的意义：LLM judge 必须做 meta-eval，不能只看 agreement 百分比。
- 对 grader observability 的意义：prompt sensitivity、leniency bias 和 kappa 应进入长期 judge health dashboard。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：human feedback、eval dataset lifecycle

## 关联

- [[concepts/LLMJudgeAIFeedbackCalibration边界]]
- [[concepts/JudgeDriftGraderObservability边界]]
- [[Research: LLM-as-judge AI feedback calibration 边界]]

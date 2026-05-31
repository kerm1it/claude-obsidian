---
address: c-000410
type: source
title: "G-Eval: NLG Evaluation using GPT-4 with Better Human Alignment"
source_url: https://arxiv.org/abs/2303.16634
source_type: paper
author: "Yang Liu et al."
published: 2023-03-29
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - ai
  - evals
  - llm-as-judge
status: active
related:
  - "[[concepts/LLMJudgeAIFeedbackCalibration边界]]"
---

# G-Eval: NLG Evaluation using GPT-4 with Better Human Alignment

**来源**：arXiv
**URL**：https://arxiv.org/abs/2303.16634
**发布时间**：2023-03-29

## 摘要

论文提出 G-Eval：用 GPT-4、chain-of-thought 和 form-filling 评估自然语言生成输出，在摘要和对话生成任务上提升与人类判断的相关性，同时指出 LLM evaluator 可能偏向 LLM 生成文本。

## 关键贡献

- 说明 LLM judge 可用于缺少参考答案的开放 NLG evaluation。
- 将 rubric / form-filling / CoT 作为 LLM judge prompt 的稳定模式。
- 提醒 LLM evaluator 也会有偏差，不能直接当成 ground truth。
- 对本 vault 的意义：LLM-as-judge 是第 6 层可用但必须校准的 grader。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：2. 模型构建层、8. 自我改进与前沿层

## 关联

- [[concepts/LLMJudgeAIFeedbackCalibration边界]]
- [[Research: LLM-as-judge AI feedback calibration 边界]]

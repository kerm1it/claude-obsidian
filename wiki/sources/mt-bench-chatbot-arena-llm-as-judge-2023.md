---
address: c-000411
type: source
title: "Judging LLM-as-a-Judge with MT-Bench and Chatbot Arena"
source_url: https://arxiv.org/abs/2306.05685
source_type: paper
author: "Lianmin Zheng et al."
published: 2023-06-09
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - ai
  - evals
  - llm-as-judge
  - chatbot-arena
status: active
related:
  - "[[concepts/LLMJudgeAIFeedbackCalibration边界]]"
  - "[[concepts/JudgeDriftGraderObservability边界]]"
---

# Judging LLM-as-a-Judge with MT-Bench and Chatbot Arena

**来源**：arXiv
**URL**：https://arxiv.org/abs/2306.05685
**发布时间**：2023-06-09

## 摘要

论文提出 MT-Bench 和 Chatbot Arena，用强 LLM judge 与 crowdsourced human preference 对齐来评估对话模型。结果显示 GPT-4 等强 judge 在特定设置下可以达到接近人类偏好的 agreement。

## 关键贡献

- 将 LLM-as-judge 推入主流对话模型评测。
- 说明 pairwise / arena 评测能捕捉开放对话质量。
- 也使 position bias、verbosity bias、self-enhancement 等后续问题变得重要。
- 对本 vault 的意义：LLM judge 能扩展 eval，但必须绑定任务、prompt、human anchor 和 bias checks。
- 后续进入长期产品 eval 时，还需要持续观测 human agreement、score drift 和 production correlation。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层、8. 自我改进与前沿层

## 关联

- [[concepts/LLMJudgeAIFeedbackCalibration边界]]
- [[concepts/JudgeDriftGraderObservability边界]]
- [[Research: LLM-as-judge AI feedback calibration 边界]]

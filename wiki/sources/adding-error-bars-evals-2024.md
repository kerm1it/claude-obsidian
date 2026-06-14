---
address: c-000446
type: source
title: "Adding Error Bars to Evals: A Statistical Approach to Language Model Evaluations"
source_url: https://arxiv.org/abs/2411.00640
source_type: paper
author: "Evan Miller"
published: 2024-11-01
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - ai
  - evals
  - statistics
  - uncertainty
status: active
related:
  - "[[concepts/EvalUncertaintyCommunicationReleaseCard边界]]"
  - "[[concepts/EvalResultInterpretationDecisionThreshold边界]]"
sources:
  - "https://www.anthropic.com/research/statistical-approach-to-model-evals"
---

# Adding Error Bars to Evals: A Statistical Approach to Language Model Evaluations

**来源**：arXiv / Anthropic research summary
**URL**：https://arxiv.org/abs/2411.00640
**发布**：2024-11-01

## 摘要

这篇论文把 language model eval 明确视为实验，并给出分析 eval 数据、比较模型差异和规划实验的统计公式。Anthropic 的配套文章强调 eval 报告要用 error bars 和实验设计思维减少统计噪声。

## 关键贡献

- 建议报告标准误、置信区间、clustered standard errors、paired differences 和实验 power。
- 强调点估计不能回答“差异是真能力还是题目抽样/随机性造成”。
- 对本 vault 的意义：release card 不能只写平均分，必须把 uncertainty 转成 gray-zone、补样本、canary 或人工复核动作。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层

## 关联

- [[concepts/EvalUncertaintyCommunicationReleaseCard边界]]
- [[Research: Eval uncertainty communication release card 边界]]

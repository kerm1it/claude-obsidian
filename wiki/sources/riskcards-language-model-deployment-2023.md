---
address: c-000448
type: source
title: "Assessing Language Model Deployment with Risk Cards"
source_url: https://arxiv.org/abs/2303.18190
source_type: paper
author: "Leon Derczynski, Hannah Rose Kirk, Vidhisha Balachandran, Sachin Kumar, Yulia Tsvetkov, M. R. Leiser, Saif Mohammad"
published: 2023-03-31
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - ai
  - risk
  - risk-cards
  - deployment
status: active
related:
  - "[[concepts/EvalUncertaintyCommunicationReleaseCard边界]]"
  - "[[concepts/IntolerableRiskThresholdStopRule边界]]"
  - "[[concepts/AISafetyOpsGovernance边界]]"
---

# Assessing Language Model Deployment with Risk Cards

**来源**：arXiv
**URL**：https://arxiv.org/abs/2303.18190
**发布**：2023-03-31

## 摘要

RiskCards 是用于结构化评估和记录语言模型应用风险的框架。它关注具体部署场景中的风险如何显现为 harm，并把风险路径、harm taxonomy 和 prompt-output 示例放进动态、参与式知识库。

## 关键贡献

- 把风险从“模型平均能力”转向“模型在特定 deployment scenario 中如何造成 harm”。
- 要求记录风险显现路径、harm taxonomy 位置和具体 prompt-output 例子。
- 对本 vault 的意义：release card 不能只写性能 improvement，还要把关键风险路径和 hard stop 条件写清楚。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层

## 关联

- [[concepts/EvalUncertaintyCommunicationReleaseCard边界]]
- [[Research: Eval uncertainty communication release card 边界]]

---
address: c-000350
type: source
title: "OpenAI fine-tuning data quality guidance"
source_url: https://platform.openai.com/docs/guides/fine-tuning-best-practices
source_type: documentation
author: "OpenAI"
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - ai
  - fine-tuning
  - data-quality
  - openai
status: active
related:
  - "[[concepts/DataQualityLabelQuality边界]]"
  - "[[concepts/微调RAG上下文工程选择框架]]"
  - "[[concepts/SyntheticDataGovernance边界]]"
---

# OpenAI fine-tuning data quality guidance

**来源**：OpenAI Platform Docs
**URL**：https://platform.openai.com/docs/guides/fine-tuning-best-practices

## 摘要

OpenAI fine-tuning best practices 强调训练数据质量对微调效果至关重要，包括修正错误、增加代表性示例、覆盖边界案例、保持格式一致，并使用验证集评估。

## 关键贡献

- 微调失败常由数据质量而非模型能力导致。
- 高质量小数据集可能比大量噪声样本更有价值。
- 对本 vault 的意义：第 2 层训练候选必须先通过第 6 层 data/label quality gate。

## 对 AI 知识体系的归属

- 主归属：2. 模型构建层
- 交叉链接：6. 评估与可靠性层

## 关联

- [[concepts/DataQualityLabelQuality边界]]
- [[concepts/SyntheticDataGovernance边界]]
- [[Research: Data quality label quality 边界]]

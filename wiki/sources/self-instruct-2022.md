---
address: c-000374
type: source
title: "Self-Instruct"
source_url: https://arxiv.org/abs/2212.10560
source_type: paper
author: "Wang et al."
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - ai
  - synthetic-data
  - instruction-tuning
status: active
related:
  - "[[concepts/SyntheticDataGovernance边界]]"
  - "[[concepts/DataQualityLabelQuality边界]]"
---

# Self-Instruct

**来源**：arXiv
**URL**：https://arxiv.org/abs/2212.10560

## 摘要

Self-Instruct 提出用模型自生成 instructions、inputs 和 outputs，再过滤无效或相似样本，用于提升 instruction-following 能力。论文还用专家写的新任务做评估。

## 关键贡献

- 展示合成 instruction data 可以在低人工标注成本下改善模型行为。
- 生成后过滤无效和相似样本，是合成数据质量门的早期范式。
- 独立 expert-written eval 说明合成训练数据需要真实或外部评估锚点。
- 对本 vault 的意义：合成数据可作为第 2 层训练候选，但必须由第 6 层过滤和 eval 决定是否进入训练。

## 对 AI 知识体系的归属

- 主归属：2. 模型构建层
- 交叉链接：6. 评估与可靠性层

## 关联

- [[concepts/SyntheticDataGovernance边界]]
- [[Research: Synthetic data governance 边界]]

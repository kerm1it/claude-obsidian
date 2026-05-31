---
address: c-000372
type: source
title: "AI models collapse when trained on recursively generated data"
source_url: https://www.nature.com/articles/s41586-024-07566-y
source_type: paper
author: "Shumailov et al."
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - ai
  - synthetic-data
  - model-collapse
status: active
related:
  - "[[concepts/SyntheticDataGovernance边界]]"
  - "[[concepts/DataQualityLabelQuality边界]]"
---

# AI models collapse when trained on recursively generated data

**来源**：Nature
**URL**：https://www.nature.com/articles/s41586-024-07566-y

## 摘要

Nature 2024 论文研究模型在递归生成数据上训练时的退化现象，提出 model collapse：模型逐代训练在前代模型生成数据上，会丢失原始数据分布的尾部信息并产生分布退化。

## 关键贡献

- 说明合成数据反馈环会造成分布缩窄和错误累积。
- 强调保留真实数据分布和数据来源非常重要。
- 对本 vault 的意义：synthetic data governance 必须防止合成样本无约束替代真实数据、污染 hold-out 或进入自我强化闭环。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：2. 模型构建层、8. 自我改进与前沿层

## 关联

- [[concepts/SyntheticDataGovernance边界]]
- [[Research: Synthetic data governance 边界]]

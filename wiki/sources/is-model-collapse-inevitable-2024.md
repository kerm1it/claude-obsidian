---
address: c-000373
type: source
title: "Is Model Collapse Inevitable?"
source_url: https://arxiv.org/abs/2404.01413
source_type: paper
author: "Gerstgrasser et al."
fetched: 2026-05-30
created: 2026-05-30
confidence: medium
tags:
  - ai
  - synthetic-data
  - model-collapse
status: active
related:
  - "[[concepts/SyntheticDataGovernance边界]]"
  - "[[concepts/DataQualityLabelQuality边界]]"
---

# Is Model Collapse Inevitable?

**来源**：arXiv
**URL**：https://arxiv.org/abs/2404.01413

## 摘要

这篇 2024 arXiv 论文研究合成数据反馈环和 model collapse，在语言模型、分子构象 diffusion model 和图像 VAE 上实验。论文区分“用每代合成数据替换真实数据”和“把合成数据与原始真实数据累积在一起”两种设置。

## 关键贡献

- 确认用递归生成数据替换真实数据会趋向 model collapse。
- 显示在实验设置中，累积真实数据和 successive synthetic data 可以避免 collapse。
- 对本 vault 的意义：合成数据治理不应简单禁止合成数据，而应禁止它替代真实数据锚点和独立 hold-out。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：2. 模型构建层、8. 自我改进与前沿层

## 关联

- [[concepts/SyntheticDataGovernance边界]]
- [[Research: Synthetic data governance 边界]]

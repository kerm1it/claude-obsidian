---
address: c-000178
type: source
title: "Distilling the Knowledge in a Neural Network"
source_url: https://arxiv.org/abs/1503.02531
source_type: paper
author: "Hinton, Vinyals, Dean"
published: 2015
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - distillation
  - paper
status: active
related:
  - "[[concepts/蒸馏传承]]"
  - "[[domains/AI知识体系]]"
---

# Distilling the Knowledge in a Neural Network

**来源**：arXiv:1503.02531
**作者**：Geoffrey Hinton, Oriol Vinyals, Jeff Dean
**发布时间**：2015

## 摘要

知识蒸馏的经典论文：把 ensemble 或大模型的知识压缩进一个更易部署的模型。它解决的核心问题是部署成本与模型性能之间的冲突。

## 关键贡献

- 说明多个模型平均预测虽然强，但部署昂贵。
- 蒸馏把复杂模型或 ensemble 的行为迁移到单个学生模型。
- 现代 LLM 产品中的“Flash / mini / small”路线仍在复用这一原语：用强模型输出训练更便宜的模型。

## 对 AI 知识体系的归属

- 主归属：2. 模型构建层
- 交叉链接：3. 推理与能力层、7. 产品与组织层
- 已有概念：[[concepts/蒸馏传承]]

## 关联

- [[sources/openai-model-distillation-2024]]
- [[sources/gemini-coleads-origins-2026-05-30]]
- [[domains/AI知识体系]]

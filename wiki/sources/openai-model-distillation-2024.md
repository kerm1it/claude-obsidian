---
address: c-000180
type: source
title: "Model Distillation in the API"
source_url: https://openai.com/index/api-model-distillation/
source_type: product-doc
author: "OpenAI"
published: 2024-10-01
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - distillation
  - fine-tuning
  - evals
status: active
related:
  - "[[concepts/蒸馏传承]]"
  - "[[domains/AI知识体系]]"
  - "[[concepts/SyntheticDataGovernance边界]]"
---

# Model Distillation in the API

**来源**：OpenAI
**URL**：https://openai.com/index/api-model-distillation/
**发布时间**：2024-10-01

## 摘要

OpenAI 的 Model Distillation 介绍了一个工程化蒸馏流程：用强模型输出生成数据，再用这些数据 fine-tune 更便宜的模型，并用 eval 衡量是否可部署。

## 关键贡献

- 把蒸馏从论文概念变成平台工作流：Stored Completions → Evals → Fine-tuning。
- 说明蒸馏不只是模型压缩，也是产品成本、延迟和质量之间的工程权衡。
- 强调 distillation inherently iterative：需要反复生成数据、训练、评估。

## 对 AI 知识体系的归属

- 主归属：2. 模型构建层
- 交叉链接：6. 评估与可靠性层、7. 产品与组织层
- 相关概念：[[concepts/蒸馏传承]]、[[concepts/Eval驱动开发]]

## 关联

- [[sources/distilling-knowledge-neural-network-2015]]
- [[domains/AI知识体系]]
- [[concepts/SyntheticDataGovernance边界]]

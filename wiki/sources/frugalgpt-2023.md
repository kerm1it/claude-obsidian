---
address: c-000292
type: source
title: "FrugalGPT: How to Use Large Language Models While Reducing Cost and Improving Performance"
source_url: https://arxiv.org/abs/2305.05176
source_type: paper
author: "Lingjiao Chen, Matei Zaharia, James Zou"
published: 2023-05-09
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - llm-cascade
  - cost-optimization
  - model-routing
status: active
related:
  - "[[concepts/ModelRoutingMixture边界]]"
  - "[[concepts/Serving成本延迟边界]]"
---

# FrugalGPT

**来源**：arXiv
**URL**：https://arxiv.org/abs/2305.05176

## 摘要

FrugalGPT 研究如何在使用 LLM API 时降低成本并保持或提升性能。论文提出三类策略：prompt adaptation、LLM approximation、LLM cascade，并用 FrugalGPT 作为 LLM cascade 的实例。

## 关键贡献

- 指出不同 LLM API 的价格结构可能差异巨大，规模化调用时成本成为核心问题。
- LLM cascade 学习对不同 query 使用不同组合的模型，以减少成本并维持质量。
- 论文报告 FrugalGPT 可在实验中以显著成本下降匹配强模型表现，或在相同成本下提升准确率。
- 对本 vault 的意义：cascade 是 model routing 的基础形态，适合先由弱模型处理，失败或低置信时再升级。

## 对 AI 知识体系的归属

- 主归属：3. 推理与能力层
- 交叉链接：6. 评估与可靠性层、7. 产品与组织层
- 作用：提供 cheap-first / cascade routing 的早期框架。

## 关联

- [[concepts/ModelRoutingMixture边界]]
- [[Research: Model routing mixture 边界]]

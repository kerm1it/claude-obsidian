---
address: c-000295
type: source
title: "Switch Transformers"
source_url: https://arxiv.org/abs/2101.03961
source_type: paper
author: "William Fedus, Barret Zoph, Noam Shazeer"
published: 2021-01-11
journal: "JMLR 2022"
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - mixture-of-experts
  - transformer
  - model-architecture
status: active
related:
  - "[[concepts/ModelRoutingMixture边界]]"
  - "[[concepts/ScalingLaws]]"
  - "[[concepts/蒸馏传承]]"
---

# Switch Transformers

**来源**：arXiv / JMLR
**URL**：https://arxiv.org/abs/2101.03961

## 摘要

Switch Transformer 是 Mixture-of-Experts 架构的代表：模型内部为每个输入选择不同专家参数，以稀疏激活方式扩展参数量，同时保持计算成本相对受控。

## 关键贡献

- MoE 与 dense model 不同：不是所有输入复用同一组参数，而是按输入选择专家。
- Switch Transformer 简化了 MoE routing algorithm，降低通信和计算成本，并改善训练稳定性。
- 论文报告在相同计算资源下提高预训练速度，并能训练到万亿参数级别。
- 大稀疏模型也可蒸馏到小 dense 模型，保留部分质量收益。

## 对 AI 知识体系的归属

- 主归属：2. 模型构建层
- 交叉链接：3. 推理与能力层
- 作用：把 internal MoE 与 application-level model routing 区分开。前者是模型架构，后者是推理时系统策略。

## 关联

- [[concepts/ModelRoutingMixture边界]]
- [[concepts/蒸馏传承]]
- [[Research: Model routing mixture 边界]]

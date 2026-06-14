---
address: c-000293
type: source
title: "Optimizing Model Selection for Compound AI Systems"
source_url: https://arxiv.org/abs/2502.14815
source_type: paper
author: "Lingjiao Chen et al."
published: 2025-02-20
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - compound-ai
  - model-selection
  - multi-agent
status: active
related:
  - "[[concepts/ModelRoutingMixture边界]]"
  - "[[concepts/AgentHarness与TraceEval]]"
---

# Optimizing Model Selection for Compound AI Systems

**来源**：arXiv
**URL**：https://arxiv.org/abs/2502.14815

## 摘要

这篇论文研究 compound AI systems 中的模型选择问题：当系统由多个 LLM call 或模块组成时，每个模块应该使用哪个模型。论文提出 LLMSelector，用线性规模的 API calls 近似解决指数级模型分配空间。

## 关键贡献

- 在 self-refine、multi-agent debate 等系统中，模型选择显著影响端到端质量。
- 每个模块都用最强模型不一定是最优成本方案；每个模块都用同一模型也可能损失质量。
- LLMSelector 迭代选择模块，并为其分配估计模块表现最好的模型。
- 实验报告在多种 compound systems 中，比所有模块使用同一模型有明显准确率提升。

## 对 AI 知识体系的归属

- 主归属：5. Agent 系统层
- 交叉链接：3. 推理与能力层、6. 评估与可靠性层
- 作用：说明 routing 在 agent/compound system 中会变成 per-module model allocation。

## 关联

- [[concepts/ModelRoutingMixture边界]]
- [[concepts/AgentHarness与TraceEval]]
- [[Research: Model routing mixture 边界]]

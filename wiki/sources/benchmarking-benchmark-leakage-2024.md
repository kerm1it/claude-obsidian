---
address: c-000302
type: source
title: "Benchmarking Benchmark Leakage in Large Language Models"
source_url: https://arxiv.org/abs/2404.18824
source_type: paper
author: "Zhen Guo et al."
published: 2024-04-29
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - benchmark-leakage
  - evals
  - contamination
status: active
related:
  - "[[concepts/RewardHackingEvalOverfitting边界]]"
  - "[[concepts/Agent评估体系]]"
  - "[[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]"
---

# Benchmarking Benchmark Leakage in Large Language Models

**来源**：arXiv
**URL**：https://arxiv.org/abs/2404.18824
**发布时间**：2024-04-29

## 摘要

论文研究 LLM benchmark leakage：benchmark 数据可能出现在训练或调参数据中，导致评测分数高估真实能力。作者提出检测 pipeline，并建议使用 Benchmark Transparency Card 记录 benchmark 使用情况。

## 关键贡献

- Benchmark leakage 会污染模型能力比较，尤其在公开 benchmark 被反复优化时。
- Perplexity 和 n-gram accuracy 可作为检测疑似泄漏的信号。
- Benchmark Transparency Card 是治理方向：记录 benchmark 是否参与训练、调参或选择。
- 对本 vault 的意义：公开榜单不能作为第 6 层唯一质量门。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：2. 模型构建层、7. 产品与组织层
- 作用：提供 eval overfitting / leakage 的实证框架，并支持 [[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界|benchmark governance]] 中的 transparency card、split isolation 和 contamination check。

## 关联

- [[concepts/RewardHackingEvalOverfitting边界]]
- [[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]
- [[Research: Reward hacking eval overfitting 边界]]

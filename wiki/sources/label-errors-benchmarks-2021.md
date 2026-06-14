---
address: c-000351
type: source
title: "Pervasive Label Errors in Test Sets"
source_url: https://arxiv.org/abs/2103.14749
source_type: paper
author: "Northcutt et al."
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - ai
  - label-quality
  - benchmarks
  - evals
status: active
related:
  - "[[concepts/DataQualityLabelQuality边界]]"
  - "[[concepts/RewardHackingEvalOverfitting边界]]"
---

# Pervasive Label Errors in Test Sets

**来源**：arXiv / NeurIPS Datasets and Benchmarks
**URL**：https://arxiv.org/abs/2103.14749

## 摘要

Pervasive Label Errors in Test Sets 研究常用视觉、语言和音频 benchmark 测试集中的标签错误，并分析这些错误如何影响模型选择和 benchmark 稳定性。

## 关键贡献

- Test/eval label 也会错，不能默认 hold-out 是真理。
- 小比例标签错误也可能改变 benchmark ranking 和模型选择。
- 对本 vault 的意义：第 6 层 eval 样本质量和 label quality 是可靠性核心，而不是数据集发布后的固定事实。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：2. 模型构建层

## 关联

- [[concepts/DataQualityLabelQuality边界]]
- [[Research: Data quality label quality 边界]]

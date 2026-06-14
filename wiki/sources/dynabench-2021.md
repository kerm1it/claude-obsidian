---
address: c-000398
type: source
title: "Dynabench: Rethinking Benchmarking in NLP"
source_url: https://arxiv.org/abs/2104.14337
source_type: paper
author: "Kiela et al."
date_published: 2021-04-29
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - evals
  - dynamic-benchmark
  - benchmark
status: active
related:
  - "[[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]"
---

# Dynabench: Rethinking Benchmarking in NLP

**来源**：arXiv / NAACL 2021
**URL**：https://arxiv.org/abs/2104.14337

## 摘要

Dynabench 反思静态 NLP benchmark：模型很快在固定 benchmark 上取得高分，却仍在简单挑战样本和真实场景失败。它提出动态数据收集和人机在环 benchmark 平台。

## 关键贡献

- 将 benchmark 从静态测试集推进到动态、对抗式、持续收集的过程。
- 强调模型和人类共同发现当前系统弱点。
- 对本 vault 的意义：eval dataset lifecycle 必须包含 refresh、adversarial collection 和 retirement，而不是永远维护同一批题。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：8. 自我改进与前沿层

## 关联

- [[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]
- [[Research: Evaluation dataset lifecycle benchmark governance 边界]]

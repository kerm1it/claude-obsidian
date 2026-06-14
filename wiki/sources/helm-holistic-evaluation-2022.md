---
address: c-000397
type: source
title: "Holistic Evaluation of Language Models"
source_url: https://arxiv.org/abs/2211.09110
source_type: paper
author: "Liang et al."
date_published: 2022-11-16
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - evals
  - benchmark
  - helm
status: active
related:
  - "[[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]"
  - "[[concepts/EvalPortfolioMetricHierarchy边界]]"
---

# Holistic Evaluation of Language Models

**来源**：arXiv / Stanford CRFM
**URL**：https://arxiv.org/abs/2211.09110

## 摘要

HELM 提出 holistic evaluation，以多场景、多指标方式评估语言模型，覆盖 accuracy、calibration、robustness、fairness、bias、toxicity、efficiency 等指标，并强调透明发布 prompts 和 completions。

## 关键贡献

- 反对单一指标或单一任务代表模型整体能力。
- 将 benchmark 组织成 scenario、adaptation、metric 的多维评估框架。
- 对本 vault 的意义：benchmark governance 要记录评估覆盖和指标选择，不能只维护一个总分榜。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层

## 关联

- [[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]
- [[concepts/EvalPortfolioMetricHierarchy边界]]
- [[Research: Evaluation dataset lifecycle benchmark governance 边界]]

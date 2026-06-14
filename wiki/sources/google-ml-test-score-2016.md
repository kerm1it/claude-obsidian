---
address: c-000474
type: source
title: "What's your ML test score? A rubric for ML production systems"
source_url: https://research.google/pubs/whats-your-ml-test-score-a-rubric-for-ml-production-systems/
source_type: paper
author: "Breck et al."
date_published: 2016
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - mlops
  - testing
  - monitoring
  - reliability
status: active
related:
  - "[[concepts/EvalPortfolioMetricHierarchy边界]]"
  - "[[concepts/EvidenceFreshnessStaleProof边界]]"
  - "[[concepts/PostReleaseEvalDrift边界]]"
---

# What's Your ML Test Score?

**来源**：Google Research
**URL**：https://research.google/pubs/whats-your-ml-test-score-a-rubric-for-ml-production-systems/

## 摘要

Google 的 ML Test Score 提出生产 ML 系统的测试和监控 rubric。论文指出真实生产 ML 系统比离线实验复杂得多，testing 和 monitoring 是评估 production readiness 的核心。

## 关键贡献

- 把 ML 可靠性从模型 accuracy 扩展到 data tests、model tests、infrastructure tests 和 monitoring tests。
- 强调“多少测试和监控才足够”是生产系统问题，不是单一 benchmark 问题。
- 对本 vault 的意义：eval portfolio 必须包含工程、数据、监控和发布证据，而不能只包含模型任务分数。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层

## 关联

- [[concepts/EvalPortfolioMetricHierarchy边界]]
- [[concepts/EvidenceFreshnessStaleProof边界]]
- [[Research: Eval portfolio metric hierarchy 边界]]

---
address: c-000481
type: source
title: "Expecting the Unexpected: Monitoring for Drift in ML Systems"
source_url: https://www.sei.cmu.edu/blog/expecting-the-unexpected-monitoring-for-drift-in-ml-systems/
source_type: engineering-blog
author: "Carnegie Mellon Software Engineering Institute"
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - drift
  - ml-monitoring
  - concept-drift
status: active
related:
  - "[[concepts/EvidenceFreshnessStaleProof边界]]"
  - "[[concepts/PostReleaseEvalDrift边界]]"
---

# Expecting the Unexpected: Monitoring for Drift in ML Systems

**来源**：CMU Software Engineering Institute
**URL**：https://www.sei.cmu.edu/blog/expecting-the-unexpected-monitoring-for-drift-in-ml-systems/

## 摘要

CMU SEI 文章区分 data drift、concept drift 和 label drift，并讨论 drift detection 的不同方式。文章指出，变化是否需要行动取决于它是否影响模型性能或决策边界，而不仅是输入分布发生变化。

## 关键贡献

- 区分 feature/data drift、concept drift、label drift。
- 强调 drift 类型不同，对生产模型影响也不同。
- 指出直接监控 performance metric 更贴近优化目标，但生产标签常常缺失。
- 对本 vault 的意义：evidence freshness 需要判断“变化是否影响 claim”，不能把所有 drift 都等同于证据失效。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层

## 关联

- [[concepts/EvidenceFreshnessStaleProof边界]]
- [[Research: Evidence freshness stale proof 边界]]

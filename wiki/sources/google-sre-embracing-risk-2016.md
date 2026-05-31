---
address: c-000493
type: source
title: "Google SRE: Embracing Risk"
source_url: https://sre.google/sre-book/embracing-risk/
source_type: book-chapter
author: "Google SRE"
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - sre
  - risk
  - error-budget
  - release-governance
status: active
related:
  - "[[concepts/MetricConflictResolution边界]]"
---

# Google SRE: Embracing Risk

**来源**：Google SRE Book
**URL**：https://sre.google/sre-book/embracing-risk/

## 摘要

Google SRE 的 Embracing Risk 章节说明可靠性目标不是 100%，而是在用户满意、成本和创新速度之间选择可接受风险水平。Error budget 是把可靠性和发布速度冲突显式化的控制环。

## 关键贡献

- 可用性越接近 100%，成本和复杂度越高。
- SLO 和 error budget 将可靠性风险变成可管理的发布预算。
- Error budget 让产品开发和 SRE 共享同一套冲突解决机制。
- 对本 vault 的意义：AI metric conflict 也需要显式风险预算和优先级，而不是临时用业务压力压过 guardrail。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层

## 关联

- [[concepts/MetricConflictResolution边界]]
- [[Research: Metric conflict resolution 边界]]

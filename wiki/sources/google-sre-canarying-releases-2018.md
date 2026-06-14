---
address: c-000494
type: source
title: "Google SRE Workbook: Canarying Releases"
source_url: https://sre.google/workbook/canarying-releases/
source_type: book-chapter
author: "Google SRE"
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - sre
  - canary
  - release-gate
  - risk-management
status: active
related:
  - "[[concepts/MetricConflictResolution边界]]"
---

# Google SRE Workbook: Canarying Releases

**来源**：Google SRE Workbook
**URL**：https://sre.google/workbook/canarying-releases/

## 摘要

Google SRE Workbook 的 Canarying Releases 章节说明如何通过小流量、分阶段、指标驱动的 rollout 降低发布风险。Canary 将不确定的 release decision 转成逐步观察和停止规则。

## 关键贡献

- Canary 把潜在缺陷的影响限制在较小流量。
- 发布速度和可靠性可以通过分阶段 rollout 和 error budget 共同管理。
- Canary 需要选择能代表用户影响和系统健康的指标。
- 对本 vault 的意义：当 AI eval 指标冲突但风险不属于 hard stop，可用 canary、shadow、limited rollout 来收集线上证据，而不是直接全量发布。

## 对 AI 知识体系的归属

- 主归属：7. 产品与组织层
- 交叉链接：6. 评估与可靠性层

## 关联

- [[concepts/MetricConflictResolution边界]]
- [[Research: Metric conflict resolution 边界]]

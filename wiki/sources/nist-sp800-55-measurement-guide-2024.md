---
address: c-000536
type: source
title: "NIST SP 800-55 Vol. 1 Measurement Guide for Information Security"
source_url: https://csrc.nist.gov/pubs/sp/800/55/v1/final
source_type: standard
author: "NIST"
date_published: 2024-12-04
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - nist
  - metrics
  - measurement
  - governance
status: active
related:
  - "[[concepts/OverrideDebtExceptionAnalyticsDashboard边界]]"
  - "[[concepts/DashboardCalibrationGovernanceMetricQuality边界]]"
---

# NIST SP 800-55 Vol. 1 Measurement Guide for Information Security

**来源**：NIST SP 800-55 Vol. 1
**URL**：https://csrc.nist.gov/pubs/sp/800/55/v1/final

## 摘要

NIST SP 800-55 Vol. 1 提供如何开发、选择、优先级排序和评估 information security measures 的指南，用来判断现有 policies、procedures 和 controls 是否足够。

## 关键贡献

- Measures 要服务管理决策，而不是只做报表。
- 指标需要选择、优先级排序和定期评价，避免低价值指标占用注意力。
- 目标是支持风险管理和资源分配。
- 对本 vault 的意义：override debt dashboard 应选择能触发治理动作的指标，如过期例外、续期、incident conversion 和 monitor coverage。
- 对 dashboard calibration 的意义：指标需要被选择、优先级排序和定期评价，不能只因为容易采集就进入治理看板。

## 对 AI 知识体系的归属

- 主归属：7. 产品与组织层
- 交叉链接：6. 评估与可靠性层

## 关联

- [[concepts/OverrideDebtExceptionAnalyticsDashboard边界]]
- [[concepts/DashboardCalibrationGovernanceMetricQuality边界]]
- [[Research: Override debt exception analytics dashboard 边界]]
- [[Research: Dashboard calibration governance metric quality 边界]]

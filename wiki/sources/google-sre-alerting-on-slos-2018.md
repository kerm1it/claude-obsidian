---
address: c-000564
type: source
title: "Google SRE Alerting on SLOs"
source_url: https://sre.google/workbook/alerting-on-slos/
source_type: book-chapter
author: "Google SRE"
date_published: 2018
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - sre
  - slo
  - alerting
  - error-budget
status: active
related:
  - "[[concepts/DashboardCalibrationGovernanceMetricQuality边界]]"
  - "[[concepts/EvalResultInterpretationDecisionThreshold边界]]"
---

# Google SRE Alerting on SLOs

**来源**：Google SRE Workbook
**URL**：https://sre.google/workbook/alerting-on-slos/

## 摘要

Google SRE Workbook 的 Alerting on SLOs 章节将 SLO、error budget、burn rate、window 和 threshold 组合成可调 alerting strategy，用来平衡及时发现问题和避免低信号告警。

## 关键贡献

- SLO alerting 需要把 threshold、duration 和 window 绑定到用户影响和 error budget。
- 多窗口、多 burn-rate 告警是防守 SLO 的常用策略。
- 低流量服务可能需要调整 SLO、窗口、合成流量或聚合服务，避免指标误导。
- 对本 vault 的意义：dashboard metric 需要阈值校准和误报/漏报权衡，不能把所有异常都当成治理行动。

## 对 AI 知识体系的归属

- 主归属：7. 产品与组织层
- 交叉链接：6. 评估与可靠性层

## 关联

- [[concepts/DashboardCalibrationGovernanceMetricQuality边界]]
- [[concepts/EvalResultInterpretationDecisionThreshold边界]]
- [[Research: Dashboard calibration governance metric quality 边界]]

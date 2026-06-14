---
address: c-000537
type: source
title: "NIST SP 800-137 Information Security Continuous Monitoring"
source_url: https://csrc.nist.gov/pubs/sp/800/137/final
source_type: standard
author: "NIST"
date_published: 2011-09
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - nist
  - continuous-monitoring
  - risk-management
  - governance
status: active
related:
  - "[[concepts/OverrideDebtExceptionAnalyticsDashboard边界]]"
  - "[[concepts/DashboardCalibrationGovernanceMetricQuality边界]]"
---

# NIST SP 800-137 Information Security Continuous Monitoring

**来源**：NIST SP 800-137
**URL**：https://csrc.nist.gov/pubs/sp/800/137/final

## 摘要

NIST SP 800-137 描述 information security continuous monitoring strategy 和 program，目标是持续获得资产、威胁、漏洞与 control effectiveness 的可见性，并在 observation 显示控制不足时及时响应风险。

## 关键贡献

- Monitoring 不是看板，而是持续支持 risk management decisions。
- 有效监控要对齐 risk tolerance，并能反映 controls 是否仍充分。
- 当控制不足时，监控结果应触发风险响应。
- 对本 vault 的意义：override debt dashboard 应把例外、续期和过期状态视为 control effectiveness 信号，驱动 review、freeze、deny renewal 或 backlog。
- 对 dashboard calibration 的意义：management dashboard 必须基于组织政策、可量化指标和 meaningful data，并服务风险响应。

## 对 AI 知识体系的归属

- 主归属：7. 产品与组织层
- 交叉链接：6. 评估与可靠性层

## 关联

- [[concepts/OverrideDebtExceptionAnalyticsDashboard边界]]
- [[concepts/DashboardCalibrationGovernanceMetricQuality边界]]
- [[Research: Override debt exception analytics dashboard 边界]]
- [[Research: Dashboard calibration governance metric quality 边界]]

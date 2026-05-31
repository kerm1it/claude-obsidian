---
address: c-000563
type: source
title: "Google SRE Monitoring Distributed Systems"
source_url: https://sre.google/sre-book/monitoring-distributed-systems/
source_type: book-chapter
author: "Google SRE"
date_published: 2016
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - sre
  - monitoring
  - metrics
  - alerting
status: active
related:
  - "[[concepts/DashboardCalibrationGovernanceMetricQuality边界]]"
---

# Google SRE Monitoring Distributed Systems

**来源**：Google SRE Book
**URL**：https://sre.google/sre-book/monitoring-distributed-systems/

## 摘要

Google SRE 的 monitoring 章节说明监控和告警应让系统在坏掉或即将坏掉时通知人，并强调四个黄金信号：latency、traffic、errors、saturation。

## 关键贡献

- 告警不应因为“看起来有点奇怪”就触发，而应围绕真实问题和可行动响应。
- 四个黄金信号帮助从用户可感知症状出发，而不是只盯内部实现细节。
- 过度混合 profiling、debugging、log analysis、traffic inspection 等系统会让 monitoring 复杂脆弱。
- 对本 vault 的意义：governance dashboard 也要区分 action signal、diagnostic signal 和 exploratory signal。

## 对 AI 知识体系的归属

- 主归属：7. 产品与组织层
- 交叉链接：6. 评估与可靠性层

## 关联

- [[concepts/DashboardCalibrationGovernanceMetricQuality边界]]
- [[Research: Dashboard calibration governance metric quality 边界]]

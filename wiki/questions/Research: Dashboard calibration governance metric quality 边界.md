---
address: c-000561
type: synthesis
title: "Research: Dashboard calibration governance metric quality 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - research
  - ai
  - governance
  - dashboard
  - metrics
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/DashboardCalibrationGovernanceMetricQuality边界]]"
  - "[[concepts/OverrideDebtExceptionAnalyticsDashboard边界]]"
  - "[[concepts/ReleaseGateDebtBypassDetection边界]]"
sources:
  - "[[sources/nist-sp800-55-measurement-guide-2024]]"
  - "[[sources/nist-sp800-55-vol2-measurement-program-2024]]"
  - "[[sources/nist-sp800-137-continuous-monitoring-2011]]"
  - "[[sources/nist-ai-rmf-playbook-monitoring-responsibility-2026]]"
  - "[[sources/google-sre-monitoring-distributed-systems-2016]]"
  - "[[sources/google-sre-alerting-on-slos-2018]]"
  - "[[sources/dora-software-delivery-performance-metrics-2026]]"
  - "[[sources/microsoft-responsible-ai-dashboard-2026]]"
---

# Research: Dashboard calibration governance metric quality 边界

## Overview

本轮研究关注 governance dashboard 是否能作为决策仪器。结论是：dashboard calibration / governance metric quality 主属第 7 层产品与组织层，因为它管理的是组织如何用指标触发 review、freeze、rollback、deny renewal、budget 和 backlog，而不是单个 eval 的数学计算。

## Key Findings

- NIST SP 800-55 Vol. 1 将 measures 视为判断 policy、procedure、control adequacy 的工具，并强调选择、优先级和评价指标。(Source: [[sources/nist-sp800-55-measurement-guide-2024]])
- NIST SP 800-55 Vol. 2 把 measurement program 当作组织化过程，而不是一次性报表；这支持把 dashboard metric 写成有 owner、cadence、review 和 communication path 的 measurement system。(Source: [[sources/nist-sp800-55-vol2-measurement-program-2024]])
- NIST SP 800-137 描述 management dashboard 应基于组织政策、可量化 performance metrics 和 meaningful data，并服务持续监控与风险管理。(Source: [[sources/nist-sp800-137-continuous-monitoring-2011]])
- NIST AI RMF Playbook 要求部署后监控 appropriate performance metrics，记录 metric selection criteria，并在既有指标不足时开发新指标。(Source: [[sources/nist-ai-rmf-playbook-monitoring-responsibility-2026]])
- Google SRE monitoring 反对因为“看起来奇怪”就触发告警，强调以用户可感知症状、四个黄金信号和清晰系统边界降低噪音。(Source: [[sources/google-sre-monitoring-distributed-systems-2016]])
- Google SRE SLO alerting 用 burn rate、window 和 threshold 把指标转成可调告警，说明 dashboard metric 需要决策阈值和误报/漏报权衡。(Source: [[sources/google-sre-alerting-on-slos-2018]])
- DORA 把软件交付指标组织成 throughput 和 instability，并在 2024/2026 口径中加入 rework 维度，说明治理指标会随实践校准而演化。(Source: [[sources/dora-software-delivery-performance-metrics-2026]])
- Microsoft Responsible AI dashboard 把 model overview、error analysis、fairness、data analysis、interpretability 和 cohorts 组合起来，说明 dashboard 要支持分组分析和可分享证据，而不是一个总分。(Source: [[sources/microsoft-responsible-ai-dashboard-2026]])

## Stable Classification

- 主归属：7. 产品与组织层
- 交叉链接：6. 评估与可靠性层
- 稳定判断：第 6 层产生 metrics；第 7 层决定这些 metrics 能否被 dashboard 化、阈值化、行动化，并持续校准它们是否预测真实风险和改进真实结果。

## Engineering Boundary

稳定链路是：`decision inventory -> metric claim -> metric definition and lineage -> data quality check -> outcome calibration -> trust tier -> threshold/action ladder -> post-action review -> refresh or retire`。

核心不是再做一张 prettier dashboard，而是给每个指标写清楚它支持什么决策、如何计算、何时 stale、谁负责、超阈值后做什么、事后如何证明这个动作有效。

## Evaluation

- Action precision：dashboard 触发行动后，有多少被事后证明正确。
- Missed risk：dashboard 没有触发但随后发生事故、绕过、过期例外或用户影响的比例。
- Calibration drift：指标与真实 outcome、incident conversion、rollback、human review 的关系是否变弱。
- Coverage：高风险 product/risk/artifact/provider slice 是否有指标。
- Gaming：指标改善但真实质量或治理结果没有改善。

## Open Questions

- 低频高风险 AI 事故样本不足时，governance dashboard 如何结合 tabletop、near miss、synthetic stress 和 expert review 做校准？
- 哪些 dashboard 指标应该进入 release freeze 或 deny renewal，哪些只能作为诊断信号？
- AI 产品中的用户伤害、隐私风险、policy bypass 和 model drift 是否能共享一套 dashboard trust tier？

## Sources

- [[sources/nist-sp800-55-measurement-guide-2024]]
- [[sources/nist-sp800-55-vol2-measurement-program-2024]]
- [[sources/nist-sp800-137-continuous-monitoring-2011]]
- [[sources/nist-ai-rmf-playbook-monitoring-responsibility-2026]]
- [[sources/google-sre-monitoring-distributed-systems-2016]]
- [[sources/google-sre-alerting-on-slos-2018]]
- [[sources/dora-software-delivery-performance-metrics-2026]]
- [[sources/microsoft-responsible-ai-dashboard-2026]]

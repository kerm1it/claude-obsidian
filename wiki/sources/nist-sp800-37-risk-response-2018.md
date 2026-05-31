---
address: c-000514
type: source
title: "NIST SP 800-37 Rev. 2 Risk Response"
source_url: https://csrc.nist.gov/pubs/sp/800/37/r2/final
source_type: standard
author: "NIST"
date_published: 2018-12-20
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - risk-management
  - residual-risk
  - governance
status: active
related:
  - "[[concepts/OverrideGovernanceResidualRiskAcceptance边界]]"
  - "[[concepts/OverrideDebtExceptionAnalyticsDashboard边界]]"
---

# NIST SP 800-37 Rev. 2 Risk Response

**来源**：NIST SP 800-37 Rev. 2
**URL**：https://csrc.nist.gov/pubs/sp/800/37/r2/final

## 摘要

NIST SP 800-37 Rev. 2 的 Risk Management Framework 把风险响应、授权决定和持续监控连接起来。风险响应包括接受、缓解等路径，剩余风险需要被授权责任人理解、记录和监控。

## 关键贡献

- Risk response 不是放任风险，而是基于 risk determination 选择行动。
- Risk acceptance 需要保留 assessment deficiencies，并持续监控 risk factors。
- Authorization decision 需要明确谁能接受 residual risk。
- 对本 vault 的意义：AI override 必须写入授权、证据、监控和复审链，而不是口头绕过 release gate。
- 对 override debt dashboard 的意义：accepted residual risk 需要持续监控和复审，才能被聚合成例外债务和风险暴露。

## 对 AI 知识体系的归属

- 主归属：7. 产品与组织层
- 交叉链接：6. 评估与可靠性层

## 关联

- [[concepts/OverrideGovernanceResidualRiskAcceptance边界]]
- [[concepts/OverrideDebtExceptionAnalyticsDashboard边界]]
- [[Research: Override governance residual risk acceptance 边界]]
- [[Research: Override debt exception analytics dashboard 边界]]

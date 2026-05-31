---
address: c-000559
type: source
title: "NIST SP 800-53 CM-3 and CM-5 Change Control"
source_url: https://csrc.nist.gov/pubs/sp/800/53/r5/upd1/final
source_type: standard
author: "NIST"
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - nist
  - change-control
  - configuration-management
  - access-restrictions
status: active
related:
  - "[[concepts/ReleaseGateDebtBypassDetection边界]]"
  - "[[concepts/AISafetyOpsGovernance边界]]"
---

# NIST SP 800-53 CM-3 and CM-5 Change Control

**来源**：NIST SP 800-53 Rev. 5
**URL**：https://csrc.nist.gov/pubs/sp/800/53/r5/upd1/final

## 摘要

SP 800-53 的 Configuration Management family 中，CM-3 关注 configuration change control，CM-5 关注 access restrictions for change。两者要求变更被审查、批准、记录、监控，并限制谁能对系统执行变更。

## 关键贡献

- Change control 不是只有审批，还包括记录、监控、审查和协调。
- Access restrictions for change 将“谁能改生产系统”作为控制对象。
- 变更控制活动需要保留记录，并能支持后续评估。
- 对本 vault 的意义：AI release gate bypass 可以被视作 configuration change control 失效，检测重点是实际变更是否有审批、记录、访问限制和监控证据。

## 对 AI 知识体系的归属

- 主归属：7. 产品与组织层
- 交叉链接：6. 评估与可靠性层

## 关联

- [[concepts/ReleaseGateDebtBypassDetection边界]]
- [[concepts/AISafetyOpsGovernance边界]]
- [[Research: Release gate debt gate bypass detection 边界]]

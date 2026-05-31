---
address: c-000548
type: source
title: "NIST Privacy Framework: Data Minimization and Audit Log Governance"
source_url: https://www.nist.gov/privacy-framework/privacy-framework
source_type: framework
author: "NIST"
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - nist
  - privacy
  - audit
  - data-minimization
status: active
related:
  - "[[concepts/EvidenceMinimizationPrivacyPreservingAuditPacket边界]]"
  - "[[concepts/DataRightsPrivacyConsent边界]]"
---

# NIST Privacy Framework: Data Minimization and Audit Log Governance

**来源**：NIST Privacy Framework
**URL**：https://www.nist.gov/privacy-framework/privacy-framework

## 摘要

NIST Privacy Framework 是组织级 privacy risk management 框架。其 data processing management 控制思想把系统处理、日志和审计记录放入组织策略中，并要求处理目的、范围、保留、访问和风险控制可被管理和审查。

## 关键贡献

- Privacy risk management 应嵌入产品、系统和组织流程，而不是事后隐私审查。
- Audit/log records 需要被确定、记录、实施和审查，并结合 data minimization 原则。
- 对本 vault 的意义：AI audit packet 应有字段级 minimization matrix 和访问审计，而不是把 trace dump 当成默认证据。

## 对 AI 知识体系的归属

- 主归属：7. 产品与组织层
- 交叉链接：6. 评估与可靠性层

## 关联

- [[concepts/EvidenceMinimizationPrivacyPreservingAuditPacket边界]]
- [[concepts/DataRightsPrivacyConsent边界]]
- [[Research: Evidence minimization privacy preserving audit packet 边界]]

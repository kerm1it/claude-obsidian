---
address: c-000549
type: source
title: "NIST SP 800-53 AU-3(3): Limit PII in Audit Records"
source_url: https://csrc.nist.gov/pubs/sp/800/53/r5/upd1/final
source_type: standard
author: "NIST"
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - nist
  - audit
  - privacy
  - pii
status: active
related:
  - "[[concepts/EvidenceMinimizationPrivacyPreservingAuditPacket边界]]"
  - "[[concepts/EvidenceRetentionAuditPacketLifecycle边界]]"
---

# NIST SP 800-53 AU-3(3): Limit PII in Audit Records

**来源**：NIST SP 800-53 Rev. 5, AU-3 control enhancement
**URL**：https://csrc.nist.gov/pubs/sp/800/53/r5/upd1/final

## 摘要

NIST SP 800-53 的 AU-3 family 定义 audit record content。AU-3(3) 的核心要求是限制 audit records 中的 personally identifiable information elements，并通过 privacy risk assessment 识别允许包含的 PII 元素。

## 关键贡献

- Audit record 不是越全越好，PII 字段要按 privacy risk assessment 限定。
- 字段级记录内容属于安全与隐私共同治理范围。
- 对本 vault 的意义：AI trace、prompt、tool output、dataset row 和 user content 进入 audit packet 前，应有字段级保留和脱敏规则。

## 对 AI 知识体系的归属

- 主归属：7. 产品与组织层
- 交叉链接：6. 评估与可靠性层

## 关联

- [[concepts/EvidenceMinimizationPrivacyPreservingAuditPacket边界]]
- [[concepts/EvidenceRetentionAuditPacketLifecycle边界]]
- [[Research: Evidence minimization privacy preserving audit packet 边界]]

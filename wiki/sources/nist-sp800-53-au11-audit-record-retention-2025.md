---
address: c-000527
type: source
title: "NIST SP 800-53 AU-11 Audit Record Retention"
source_url: https://csrc.nist.gov/pubs/sp/800/53/r5/upd1/final
source_type: standard
author: "NIST"
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - nist
  - audit
  - retention
  - records-management
status: active
related:
  - "[[concepts/EvidenceRetentionAuditPacketLifecycle边界]]"
  - "[[concepts/EvidenceMinimizationPrivacyPreservingAuditPacket边界]]"
---

# NIST SP 800-53 AU-11 Audit Record Retention

**来源**：NIST SP 800-53 Rev. 5, AU-11
**URL**：https://csrc.nist.gov/pubs/sp/800/53/r5/upd1/final

## 摘要

AU-11 要求组织按照 retention policy 保留 audit records，以支持事后事件调查，并满足监管和组织信息保留要求。其增强项强调长期 audit records 必须可检索、可读取、可解释。

## 关键贡献

- Retention period 不是工具默认值，而应来自组织记录保留策略。
- Audit records 保留目标包括 incident investigation、legal/audit purpose 和组织运行需求。
- 长期检索需要格式迁移、可读设备或解释文档，避免多年后记录不可用。
- 对本 vault 的意义：AI release/eval/safety evidence packet 必须有 retention class、retrieval plan 和 interpretation context。
- 对 privacy-preserving audit packet 的意义：retention 需要和字段级最小化配套，长期证据包应优先保留能重验证明 claim 的最小充分集。

## 对 AI 知识体系的归属

- 主归属：7. 产品与组织层
- 交叉链接：6. 评估与可靠性层

## 关联

- [[concepts/EvidenceRetentionAuditPacketLifecycle边界]]
- [[concepts/EvidenceMinimizationPrivacyPreservingAuditPacket边界]]
- [[Research: Evidence retention audit packet lifecycle 边界]]

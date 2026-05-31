---
address: c-000546
type: synthesis
title: "Research: Evidence minimization privacy preserving audit packet 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - research
  - ai
  - governance
  - privacy
  - evidence
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/EvidenceMinimizationPrivacyPreservingAuditPacket边界]]"
  - "[[concepts/EvidenceRetentionAuditPacketLifecycle边界]]"
  - "[[concepts/DataRightsPrivacyConsent边界]]"
sources:
  - "[[sources/eu-gdpr-article-5-data-minimization-storage-accountability-2016]]"
  - "[[sources/nist-privacy-framework-data-minimization-audit-log-2020]]"
  - "[[sources/nist-sp800-53-au3-pii-audit-record-minimization-2025]]"
  - "[[sources/ietf-rfc9901-sd-jwt-selective-disclosure-2025]]"
  - "[[sources/w3c-vc-bbs-selective-disclosure-2026]]"
  - "[[sources/nist-sp800-53-au11-audit-record-retention-2025]]"
  - "[[sources/nist-sp800-92r1-log-management-2023]]"
  - "[[sources/slsa-source-requirements-evidence-expunging-2026]]"
---

# Research: Evidence minimization privacy preserving audit packet 边界

## Overview

本轮研究把“审计证据必须可找回、可解释、可重验”和“隐私/安全要求少收、少留、少披露”合成一个边界：privacy-preserving audit packet。它主属第 7 层产品与组织层，消费第 6 层证据，但重点是组织如何保存、展示和处置证据。

## Key Findings

- GDPR Article 5 把 data minimization、storage limitation、integrity/confidentiality 和 accountability 放在同一组原则里，说明“为了审计”也要证明处理目的和保留范围。(Source: [[sources/eu-gdpr-article-5-data-minimization-storage-accountability-2016]])
- NIST Privacy Framework 把 audit/log records 纳入 data processing management，并要求结合 data minimization 来确定、记录、实施和审查日志策略。(Source: [[sources/nist-privacy-framework-data-minimization-audit-log-2020]])
- NIST SP 800-53 AU-3(3) 明确 audit record 内容中的 PII 元素应由 privacy risk assessment 限定，直接支持字段级最小化矩阵。(Source: [[sources/nist-sp800-53-au3-pii-audit-record-minimization-2025]])
- AU-11 和 SP 800-92r1 说明 audit records 需要可保留、可检索、可解释和可处置，但它们本身不等于“全部原始日志永久保存”。(Source: [[sources/nist-sp800-53-au11-audit-record-retention-2025]]; [[sources/nist-sp800-92r1-log-management-2023]])
- SLSA source requirements 承认 legal/privacy expunging 的需求，同时要求保留请求、动作和控制机制的审计痕迹，适合映射为 tombstone/disposition record。(Source: [[sources/slsa-source-requirements-evidence-expunging-2026]])
- SD-JWT 和 W3C VC BBS 都说明选择性披露可以把“证明某些 claim”与“暴露完整 credential/log”分开，是外部审计和供应链证据披露的稳定技术方向。(Source: [[sources/ietf-rfc9901-sd-jwt-selective-disclosure-2025]]; [[sources/w3c-vc-bbs-selective-disclosure-2026]])

## Stable Classification

- 主归属：7. 产品与组织层
- 交叉链接：6. 评估与可靠性层
- 稳定判断：retention lifecycle 解决“证据怎么长期管”；privacy-preserving audit packet 解决“为了这个 claim，到底需要保留或披露哪些最小字段”。

## Engineering Boundary

稳定链路是：`audit claim -> purpose/evidence need -> sensitivity classification -> minimum proof set -> redaction/digest/encryption/selective disclosure/private annex -> scoped access -> retention/legal hold/deletion/disposition`。

关键产物不是一个脱敏工具，而是字段级 evidence minimization matrix、withheld-field manifest、private annex、selective-disclosure proof 和 tombstone/disposition record。

## Evaluation

- Minimality review：每个字段是否直接支持某个 audit claim。
- Leakage scan：PII、secret、tenant、customer text、hold-out 和 prompt 的泄漏率。
- Reverification sufficiency：最小证据是否仍能重验签名、policy decision、eval summary 和 release decision。
- Access audit：敏感 annex 的访问者、理由、时间、过期和再披露是否可追踪。
- Deletion conflict resolution：删除、retention、legal hold 和 audit need 冲突是否有记录化判断。

## Open Questions

- 高风险事故中，最小化证据和完整取证之间的可接受比例如何按风险层设定？
- 选择性披露 proof 能否覆盖 AI eval 的复杂 claim，还是仍需要 private annex 保存样本级证据？
- 哪些 hash / pseudonymization 在小域或跨系统关联下会变成可重新识别风险？

## Sources

- [[sources/eu-gdpr-article-5-data-minimization-storage-accountability-2016]]
- [[sources/nist-privacy-framework-data-minimization-audit-log-2020]]
- [[sources/nist-sp800-53-au3-pii-audit-record-minimization-2025]]
- [[sources/ietf-rfc9901-sd-jwt-selective-disclosure-2025]]
- [[sources/w3c-vc-bbs-selective-disclosure-2026]]
- [[sources/nist-sp800-53-au11-audit-record-retention-2025]]
- [[sources/nist-sp800-92r1-log-management-2023]]
- [[sources/slsa-source-requirements-evidence-expunging-2026]]

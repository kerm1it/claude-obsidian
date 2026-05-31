---
address: c-000526
type: research
title: "Research: Evidence retention audit packet lifecycle 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - research
  - evidence
  - audit
  - records-management
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/EvidenceRetentionAuditPacketLifecycle边界]]"
sources:
  - "[[sources/nist-sp800-53-au11-audit-record-retention-2025]]"
  - "[[sources/nist-sp800-92r1-log-management-2023]]"
  - "[[sources/nara-general-records-schedules-2025]]"
  - "[[sources/iso-15489-records-management-2016]]"
  - "[[sources/in-toto-archivista-2026]]"
  - "[[sources/slsa-source-requirements-evidence-expunging-2026]]"
  - "[[sources/slsa-verifier-provenance-bundle-2026]]"
---

# Research: Evidence retention audit packet lifecycle 边界

## 问题

第 6/7 层如何保留、压缩、检索、重验和销毁 release/eval/safety evidence 包，使 AI 系统几年后仍能解释“当时为什么发布、谁批准、证据是什么、是否还能重验”？

## 结论

Evidence retention / audit packet lifecycle 主属第 7 层，因为它处理 records policy、legal/audit purpose、长期检索、disposition 和 responsibility；它消费第 6 层 signed evidence、freshness、verifier policy 和 eval artifacts。稳定职责是：把每次 release、override、safety case 和 incident 的证据打包成带 manifest、retention class、storage tier、reverification hook 和 disposition record 的 audit packet。

稳定链路是：`decision -> evidence manifest -> packet assembly -> storage tier -> retrieval/reverify -> legal hold/disposition -> destruction or preservation record`。

## 关键发现

- NIST SP 800-53 AU-11 要求 audit records 按组织 retention policy 保存，以支持 after-the-fact investigation 和 regulatory / organizational requirements。(Source: [[sources/nist-sp800-53-au11-audit-record-retention-2025]])
- NIST SP 800-92r1 把 log management 定义为 generation、transmission、storage、access 和 disposal 的全流程，并强调 records 要保存足够时间以支持调查与合规。(Source: [[sources/nist-sp800-92r1-log-management-2023]])
- NARA GRS 提供 disposition authority，说明 record retention 不只是“备份”，还包括何时销毁或转移。(Source: [[sources/nara-general-records-schedules-2025]])
- ISO 15489 把 records management 定义为 creation、capture、management、metadata、assigned responsibilities、monitoring 和 records controls 的系统。(Source: [[sources/iso-15489-records-management-2016]])
- in-toto Archivista 展示 attestation 可存入 object store，同时抽取 metadata 建 queryable graph，用 subject edge 支持按 artifact hash 查询。(Source: [[sources/in-toto-archivista-2026]])
- SLSA source requirements 要求 expunging process 被记录，并要求 source provenance contemporaneously created，说明证据删除和证据生成都应可审计。(Source: [[sources/slsa-source-requirements-evidence-expunging-2026]])
- SLSA verifier 将 `.sigstore` bundle 作为输入并可输出 verified in-toto statement 给 policy engines，说明 audit packet 应保存能重验的 bundle 和 verification material。(Source: [[sources/slsa-verifier-provenance-bundle-2026]])

## 分类决策

- 主归属：7. 产品与组织层
- 证据输入：6. 评估与可靠性层
- 上游：release card、eval result、signed bundle、VSA、verifier policy、trust root、safety case、incident evidence、override record
- 下游：audit packet、storage tier、retrieval workflow、reverification task、legal hold、disposition/destruction record

## Open Questions

- AI release evidence 的默认 retention class 应如何按 risk tier 设计？
- 高风险系统应保留原始 trace、摘要 trace，还是只保留 signed eval bundle？
- 删除请求、privacy minimization 和 audit/legal hold 冲突时，哪些 evidence 字段保留 tombstone 即可？

## 代表来源

- [[sources/nist-sp800-53-au11-audit-record-retention-2025]]
- [[sources/nist-sp800-92r1-log-management-2023]]
- [[sources/nara-general-records-schedules-2025]]
- [[sources/iso-15489-records-management-2016]]
- [[sources/in-toto-archivista-2026]]
- [[sources/slsa-source-requirements-evidence-expunging-2026]]
- [[sources/slsa-verifier-provenance-bundle-2026]]

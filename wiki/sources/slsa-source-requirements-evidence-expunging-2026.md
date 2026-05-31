---
address: c-000532
type: source
title: "SLSA v1.2 Source Requirements: Evidence, Provenance, and Expunging"
source_url: https://slsa.dev/spec/v1.2/source-requirements
source_type: specification
author: "SLSA"
fetched: 2026-05-30
created: 2026-05-30
confidence: high
tags:
  - slsa
  - provenance
  - source-control
  - expunging
status: active
related:
  - "[[concepts/EvidenceRetentionAuditPacketLifecycle边界]]"
  - "[[concepts/DataDeletionUnlearningImpact边界]]"
  - "[[concepts/EvidenceMinimizationPrivacyPreservingAuditPacket边界]]"
---

# SLSA v1.2 Source Requirements: Evidence, Provenance, and Expunging

**来源**：SLSA Source Track Requirements
**URL**：https://slsa.dev/spec/v1.2/source-requirements

## 摘要

SLSA Source Track 要求 source control system 在更高等级下保留连续、不可变的历史并生成 source provenance。规范也承认出于法律或隐私合规可能需要 expunging，但要求组织记录请求与动作，并倾向保留可审计日志。

## 关键贡献

- Source provenance 应在 revision 产生时同步生成，而不是事后补写。
- Safe expunging process 需要文档化请求、动作和控制机制。
- 删除可为了 legal/privacy compliance，但仍要考虑审计痕迹、权限和透明度。
- 对本 vault 的意义：AI evidence retention 需要同时处理“必须保留的证据”和“必须删除或匿名化的材料”，并用 tombstone/disposition record 保留可审计上下文。
- 对 privacy-preserving audit packet 的意义：expunging 后不能静默丢证，应该保留最小 tombstone、请求、authority、scope 和处置记录。

## 对 AI 知识体系的归属

- 主归属：7. 产品与组织层
- 交叉链接：6. 评估与可靠性层

## 关联

- [[concepts/EvidenceRetentionAuditPacketLifecycle边界]]
- [[concepts/DataDeletionUnlearningImpact边界]]
- [[concepts/EvidenceMinimizationPrivacyPreservingAuditPacket边界]]
- [[Research: Evidence retention audit packet lifecycle 边界]]

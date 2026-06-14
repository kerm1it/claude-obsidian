---
address: c-000498
type: source
title: "SLSA v1.2 Provenance"
source_url: https://slsa.dev/spec/v1.2/provenance
source_type: specification
author: "SLSA"
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - supply-chain
  - provenance
  - slsa
  - attestation
status: active
related:
  - "[[concepts/EvidenceAttestationSignedEvalArtifact边界]]"
---

# SLSA v1.2 Provenance

**来源**：SLSA
**URL**：https://slsa.dev/spec/v1.2/provenance

## 摘要

SLSA v1.2 将 provenance 定义为可验证信息，用来追踪 artifact 在复杂供应链中从哪里来、何时产生、如何产生。它区分 build provenance 和 source provenance，并将 provenance 视为 SLSA 不同 track 的共同概念。

## 关键贡献

- 将 provenance 定义为 artifact 的可验证来源和生成方式信息。
- 强调 provenance 需要能支撑复杂供应链中的追踪和验证。
- 对本 vault 的意义：AI eval result、model snapshot、prompt、judge、dataset 和 container 都可以被视为需要 provenance 的 artifact。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层

## 关联

- [[concepts/EvidenceAttestationSignedEvalArtifact边界]]
- [[Research: Evidence attestation signed eval artifact 边界]]

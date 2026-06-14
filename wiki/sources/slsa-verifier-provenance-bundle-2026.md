---
address: c-000533
type: source
title: "SLSA Verifier: Provenance Bundle Verification"
source_url: https://github.com/slsa-framework/slsa-verifier
source_type: open-source-repository
author: "SLSA"
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
confidence: high
tags:
  - slsa
  - verifier
  - provenance
  - attestation
status: active
related:
  - "[[concepts/EvidenceRetentionAuditPacketLifecycle边界]]"
  - "[[concepts/VerifierPolicyTrustRootRotation边界]]"
---

# SLSA Verifier: Provenance Bundle Verification

**来源**：slsa-framework/slsa-verifier
**URL**：https://github.com/slsa-framework/slsa-verifier

## 摘要

SLSA Verifier 是用于验证 SLSA provenance 和 VSA 的工具。它支持验证 artifact、image、package 和 attestation，并可输出 verified in-toto statement，供后续 policy engine 或 release workflow 消费。

## 关键贡献

- Audit packet 应保存 provenance/attestation bundle，而不是只保存 verifier 的文字结论。
- Reverification 需要 artifact digest、attestation path、source URI、builder/verifier identity 和 policy context。
- Verified in-toto statement 可以作为 policy engine 的输入，连接第 6 层证据验收与第 7 层发布治理。
- 对本 vault 的意义：AI evidence packet 要能被未来 verifier 重放验证，尤其在 trust root、policy 或 provider 变化之后。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：7. 产品与组织层

## 关联

- [[concepts/EvidenceRetentionAuditPacketLifecycle边界]]
- [[concepts/VerifierPolicyTrustRootRotation边界]]
- [[Research: Evidence retention audit packet lifecycle 边界]]

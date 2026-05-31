---
address: c-000516
type: concept
title: "Verifier Policy / Trust Root Rotation 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - evals
  - attestation
  - trust-root
  - release-gate
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/EvidenceAttestationSignedEvalArtifact边界]]"
  - "[[concepts/EvidenceFreshnessStaleProof边界]]"
  - "[[concepts/EvalUncertaintyCommunicationReleaseCard边界]]"
  - "[[concepts/ModelReleaseRollbackGate边界]]"
  - "[[concepts/MultiProviderGovernance边界]]"
  - "[[concepts/OverrideGovernanceResidualRiskAcceptance边界]]"
  - "[[concepts/EvidenceRetentionAuditPacketLifecycle边界]]"
  - "[[concepts/CrossVerifierPolicyDriftConformanceTest边界]]"
sources:
  - "[[sources/slsa-verification-summary-attestation-v1-2-2026]]"
  - "[[sources/slsa-verifying-artifacts-v1-2-2026]]"
  - "[[sources/sigstore-cosign-custom-components-trust-root-2026]]"
  - "[[sources/sigstore-keyless-root-of-trust-2026]]"
  - "[[sources/sigstore-tuf-root-update-2024]]"
  - "[[sources/tuf-root-metadata-api-2021]]"
  - "[[sources/in-toto-verify-2026]]"
  - "[[sources/sigstore-policy-controller-2026]]"
  - "[[sources/slsa-verifier-provenance-bundle-2026]]"
  - "[[sources/sigstore-cosign-attestation-policy-cue-rego-2026]]"
  - "[[sources/open-policy-agent-policy-testing-2026]]"
---

# Verifier Policy / Trust Root Rotation 边界

Verifier policy / trust root rotation 是第 6 层评估与可靠性层的证据验收边界：它定义 release gate、safety case 或 evidence ledger 在验证 signed eval artifact、model、prompt、tool、container、dataset 或 provider evidence 时，信任哪些 root、issuer、signer、builder、predicate、参数和时间窗口，并在 root、key、certificate、Rekor/CT log、TUF metadata 或 provider identity 变化时安全轮换、撤销和重验。

一句话：**attestation 让证据可验证；verifier policy 决定什么才算验证通过；trust root rotation 保证“谁可信”不会变成永不过期的隐性常量。**

## 主归属

- 主归属：6. 评估与可靠性层
- 组织接口：7. 产品与组织层
- 上游输入：signed bundle、artifact digest、provenance、VSA、TUF trusted root、Fulcio/Rekor/CT key material、builder/signer identity、provider trust boundary
- 下游输出：verification pass/fail/warn、policy decision、trust-root update、revocation action、reverification task、release-card / safety-case evidence status
- 执行接口：[[concepts/ModelReleaseRollbackGate边界]]

## 稳定链路

```text
evidence bundle / artifact / VSA
    -> verifier policy: expected subject, predicateType, builder/signer/verifier identity, issuer, parameters, freshness
    -> trust material: root CA, Rekor/CT keys, TUF trusted root, enterprise keys, provider root
    -> policy evaluation: signature, digest, identity, transparency, timestamp, expected parameters, revoked/expired roots
    -> decision: accept, warn, quarantine, rerun, reject, block release, or require override
    -> rotation lifecycle: add new root, overlap, client compatibility, revoke old root, reverify affected evidence
    -> record policy version, trust-root version, decision, owner, expiry, and audit trail
```

## Verifier Policy 字段

| 字段 | 作用 |
|---|---|
| Artifact identity | model、prompt、tool、dataset、container、release evidence 的 digest 和版本 |
| Expected predicate | provenance、test result、VSA、scan result、release claim 等允许的 predicateType |
| Trusted identities | 允许的 signer、builder、evaluator、verifier、OIDC issuer、provider 或 package ecosystem |
| Trust root set | TUF root、Fulcio CA、Rekor/CT public key、enterprise CA、hardware/key service root |
| Policy version | 哪一版 verifier policy 控制这次 gate，是否可回放审计 |
| Freshness / time | signature time、certificate validity、TUF metadata expiry、evidence valid_until |
| Rotation state | active、overlap、deprecated、revoked、emergency-blocked |
| Failure action | warn、quarantine、rerun、fallback、block release、incident、override review |

## 与相邻概念区别

- 与 [[concepts/EvidenceAttestationSignedEvalArtifact边界]]：attestation 生成可验证 evidence bundle；本页定义 verifier 如何依据 policy 和 trust root 判断它是否可被接受。
- 与 [[concepts/EvidenceFreshnessStaleProof边界]]：freshness 判断证据是否仍支持 claim；verifier policy 判断签名、身份、root、predicate 和参数是否仍可信。
- 与 [[concepts/EvidenceRetentionAuditPacketLifecycle边界]]：verifier policy 决定当前 evidence 是否通过；retention lifecycle 保存当时 policy/root 版本并在轮换、撤销或 provider 变化后触发 reverify。
- 与 [[concepts/EvalUncertaintyCommunicationReleaseCard边界]]：release card 表达证据状态；本页提供 verified / unverifiable / revoked / policy-mismatch 的机器可审查结论。
- 与 [[concepts/ModelReleaseRollbackGate边界]]：release gate 执行放行、阻断或回滚；verifier policy 给 gate 提供证据完整性和信任根判定。
- 与 [[concepts/MultiProviderGovernance边界]]：provider governance 决定 provider 是否合格；verifier policy 验证 provider 导出的签名证据、模型包和 VSA 是否来自允许身份和 root。
- 与 [[concepts/OverrideGovernanceResidualRiskAcceptance边界]]：验证失败或 root mismatch 不能静默放行；若非 hard stop，必须走有期限、有 monitor 的 override 记录。
- 与 [[concepts/CrossVerifierPolicyDriftConformanceTest边界]]：本页定义 policy 和 trust root；cross-verifier conformance test 检查 CI、release gate、admission controller 和本地 verifier 是否执行同一 policy/root 语义。
- 与 generic key management：本页不管理所有 secret，而管理 release/eval/safety verifier 消费的 trust material、policy 和轮换状态。

## 工程实践

1. 把 verifier policy 作为版本化 artifact，和 release card、safety case、evidence ledger 一起保存。
2. 对每类证据写 allowlist：predicateType、issuer、signer/verifier id、builder id、source repo、externalParameters、dataset split、artifact digest。
3. 使用 TUF 或等价机制分发 trust root；记录 root metadata version、expiry、client compatibility 和 update source。
4. 轮换 root/key 时保留 overlap window：先加入新 root，双验证一段时间，再弃用旧 root。
5. 对 emergency compromise 支持快速 revoke / blocklist，并查询哪些 release evidence、model、prompt、tool 或 dataset 受影响。
6. 验证失败要有动作矩阵：quarantine evidence、rerun eval、request re-attestation、fallback provider、hold rollout、rollback 或 incident。
7. 对第三方 VSA 记录 verifier id、policy digest 和 root of trust；不要只相信 badge 或截图。
8. 把 policy-controller / admission gate / CI gate 的配置纳入测试，避免 verifier policy 改动后 gate 行为漂移。

## 评估方式

- Policy coverage：关键 artifact 类型是否都有 predicate、identity、root、parameter 和 failure action。
- Root inventory completeness：所有 active root、issuer、verifier、provider key 是否有 owner、expiry 和 rotation plan。
- Rotation drill success：planned root rotation 是否在 overlap window 内通过新旧证据验证，旧 root 是否按期退役。
- Revocation latency：root/key/signer compromise 后，到 gate 阻断受影响证据的时间。
- Reverification coverage：root 或 policy 改变后，受影响 release card、safety case、eval evidence 是否被重验。
- Policy drift：CI、admission controller、release gate 和本地 verifier 是否执行同一 policy version。
- Unverified escape：policy mismatch、unknown root、expired metadata 或 unexpected identity 是否进入生产决策。

## 过时风险

- 具体签名格式、TUF metadata、Sigstore bundle 和 verifier 工具会变化，但 expected identity、policy version、trust root、rotation、revocation 和 re-verification 稳定。
- Keyless signing 降低了 signer key 管理负担，不消除 verifier policy 负担；组织仍要定义哪些身份、issuer 和 roots 可被接受。
- 如果 trust root 永久内嵌且没有轮换演练，签名体系会在第一次 root 更新、client incompatibility 或 key compromise 时失效。

## 一句话归类

Verifier policy / trust root rotation 主属第 6 层，是 signed eval artifact 进入第 7 层 release gate、release card、safety case 和 provider governance 前的证据验收策略边界；它不新增顶层，而是把“证据可验证”推进到“证据按当前可信策略通过验证”。

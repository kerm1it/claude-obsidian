---
address: c-000539
type: concept
title: "Cross-verifier Policy Drift / Conformance Test 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - evals
  - verifier
  - policy
  - conformance
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/VerifierPolicyTrustRootRotation边界]]"
  - "[[concepts/EvidenceAttestationSignedEvalArtifact边界]]"
  - "[[concepts/ProductionContractCompatibilityTest边界]]"
  - "[[concepts/ModelReleaseRollbackGate边界]]"
  - "[[concepts/EvidenceFreshnessStaleProof边界]]"
  - "[[concepts/EvidenceRetentionAuditPacketLifecycle边界]]"
  - "[[concepts/EvidenceMinimizationPrivacyPreservingAuditPacket边界]]"
  - "[[concepts/MultiProviderGovernance边界]]"
  - "[[concepts/MonitorOwnershipEscalationLadder边界]]"
  - "[[concepts/ReleaseGateDebtBypassDetection边界]]"
sources:
  - "[[sources/sigstore-policy-controller-2026]]"
  - "[[sources/slsa-verification-summary-attestation-v1-2-2026]]"
  - "[[sources/in-toto-verify-2026]]"
  - "[[sources/sigstore-cosign-attestation-policy-cue-rego-2026]]"
  - "[[sources/open-policy-agent-policy-testing-2026]]"
  - "[[sources/open-policy-agent-gatekeeper-gator-verify-2026]]"
  - "[[sources/kyverno-policy-testing-ci-2026]]"
  - "[[sources/google-cloud-deploy-approvals-policies-audit-2026]]"
---

# Cross-verifier Policy Drift / Conformance Test 边界

Cross-verifier policy drift / conformance test 是第 6 层评估与可靠性层的策略一致性边界：它验证 local CLI、CI、release gate、admission controller、runtime guard、第三方 VSA verifier 是否用同一 policy version、trust root、artifact identity、input bundle 和解释语义作出同样 allow / deny / warn 决策。

一句话：**verifier policy 定义“什么算通过”；cross-verifier conformance test 证明所有执行点真的按同一个规则通过。**

## 主归属

- 主归属：6. 评估与可靠性层
- 组织接口：7. 产品与组织层
- 上游输入：signed evidence bundle、verifier policy、trust root、engine version、CI config、admission controller config、release gate config、golden conformance corpus
- 下游输出：conformance report、policy drift alert、false allow / false deny finding、block / quarantine / resync / rollback / override-review action
- 执行接口：[[concepts/ModelReleaseRollbackGate边界]]、[[concepts/MonitorOwnershipEscalationLadder边界]]

## 稳定链路

```text
canonical verifier policy + trust root
    -> golden corpus: pass, fail, expired, wrong issuer, wrong predicate, stale, missing dependency, replay
    -> run corpus through local CLI, CI, release gate, admission controller, runtime guard, third-party verifier
    -> compare decision, reason code, policy digest, trust-root version, engine version, input normalization
    -> classify drift: policy version, root material, parser, predicate path, warn/enforce mode, namespace scope, stale cache
    -> action: block, warn, resync, pin version, rotate root, update tests, rollback, override review
    -> retain conformance report with release evidence
```

## Drift 类型

| 类型 | 说明 |
|---|---|
| Policy version drift | CI 使用新 policy，admission controller 仍在旧 policy |
| Trust-root drift | 本地 verifier、gate、cluster root material 不一致 |
| Engine semantic drift | Rego/CUE/CEL/validator 版本或内置函数导致结果不同 |
| Input normalization drift | artifact digest、subject、resourceUri、predicate 路径或 bundle 解析不同 |
| Mode drift | 一个点是 warn，另一个点是 enforce，导致上线行为不同 |
| Scope drift | namespace label、image pattern、provider allowlist 或 tenant scope 缺失 |
| Cache / freshness drift | admission controller 读到 stale policy、stale root 或旧 bundle |
| Delegated verifier drift | 第三方 VSA verifier 的 policy 与本地 release gate 预期不一致 |

## 与相邻概念区别

- 与 [[concepts/VerifierPolicyTrustRootRotation边界]]：verifier policy / trust root rotation 定义当前可信策略和根材料；本页测试所有执行点是否都执行同一策略。
- 与 [[concepts/EvidenceAttestationSignedEvalArtifact边界]]：attestation 证明证据未被替换；conformance test 证明不同 verifier 对证据的验收结果一致。
- 与 [[concepts/ProductionContractCompatibilityTest边界]]：production contract 测产品行为是否兼容；本页测证据验收 policy 是否跨执行点兼容。
- 与 [[concepts/ModelReleaseRollbackGate边界]]：release gate 执行发布/hold/rollback；本页防止 gate、CI、admission controller 和 runtime guard 发生验收漂移。
- 与 [[concepts/EvidenceFreshnessStaleProof边界]]：freshness 判断证据是否过期；本页检查不同 verifier 是否用同样 freshness rule。
- 与 [[concepts/EvidenceRetentionAuditPacketLifecycle边界]]：retention 保存历史证据包；本页把 conformance report 作为 release evidence 一起留存。
- 与 [[concepts/EvidenceMinimizationPrivacyPreservingAuditPacket边界]]：本页生成 conformance report；privacy-preserving packet 要求 golden corpus、decision matrix 和 report 中的用户数据、secret 与 hold-out 最小化披露。
- 与 [[concepts/ReleaseGateDebtBypassDetection边界]]：conformance test 检查 verifier policy/root 是否跨执行点一致；gate bypass detection 检查真实部署路径是否覆盖这些执行点，避免 CI/gate 正确但生产绕路。
- 与 generic unit test：本页不是测试业务代码，而是测试“验收策略在所有 enforcement points 的等价性”。

## 工程实践

1. 建立 canonical policy package：policy 文件、data 文件、trust root、expected identities、predicate types、freshness rule、engine version 和 policy digest。
2. 准备 golden corpus：合法 bundle、错 issuer、错 subject、错 predicate、过期 root、expired evidence、missing dependency、wrong resourceUri、replay、namespace scope miss。
3. 同一 corpus 同时跑 local CLI、CI check、release gate verifier、admission controller dry-run、runtime guard 和 delegated VSA verifier。
4. 输出 decision matrix：allow / deny / warn、reason code、policy digest、root version、engine version、input digest、timestamp。
5. 高风险策略 mismatch 默认 fail closed；低风险 warn/enforce mismatch 进入 owner ticket。
6. 每次 policy、trust root、engine、admission controller、provider verifier 或 release gate 更新后，必须重跑 conformance suite。
7. 对 remote policy / ConfigMapRef / URL+SHA256 / admission labels 做配置漂移检查，避免 CI 通过但集群未 enforce。
8. 把 conformance report 写入 release card 和 audit packet，便于事故后重放当时验收语义。

## 评估方式

- Conformance pass rate：所有 enforcement points 是否对 golden corpus 产生一致结果。
- False allow mismatch：某执行点放行了 canonical policy 应拒绝的 artifact。
- False deny mismatch：某执行点拒绝了 canonical policy 应放行的 artifact。
- Drift detection latency：policy/root/engine/config 漂移到被发现的时间。
- Coverage：golden corpus 是否覆盖 identity、predicate、freshness、dependency、scope、mode、cache 和 delegated verifier。
- Reproducibility：audit 时能否用历史 policy/root/engine 重放相同结果。
- Action closure：drift 是否转成 resync、pin、rollback、root rotation、policy update 或 override review。

## 过时风险

- 具体 policy language、admission controller 和 verifier 工具会变化，但 cross-verifier equivalence、golden corpus、policy digest、reason code 和 fail-closed action 稳定。
- 如果只在 CI 做 policy test，不验证 admission/runtime enforcement，就会出现“测试通过但生产没有拦”的漂移。
- 如果只看最终 allow/deny，不比较 reason code、policy digest、root version 和 input normalization，语义漂移会被隐藏。

## 一句话归类

Cross-verifier policy drift / conformance test 主属第 6 层，是 signed evidence 和 verifier policy 进入第 7 层 release gate / admission control 前的一致性验证边界；它不新增顶层，而是防止不同 verifier 对同一证据作出不同安全决策。

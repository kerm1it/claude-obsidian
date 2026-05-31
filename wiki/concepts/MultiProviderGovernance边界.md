---
address: c-000353
type: concept
title: "Multi-provider Governance 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - governance
  - multi-provider
  - vendor-management
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/ModelRoutingMixture边界]]"
  - "[[concepts/DataRightsPrivacyConsent边界]]"
  - "[[concepts/ToolRiskPermissioning边界]]"
  - "[[concepts/AISafetyOpsGovernance边界]]"
  - "[[concepts/Serving成本延迟边界]]"
  - "[[concepts/AgentIdentityDelegation边界]]"
  - "[[concepts/AIIncidentResponsePostmortem边界]]"
  - "[[concepts/ModelReleaseRollbackGate边界]]"
  - "[[concepts/ProductionContractCompatibilityTest边界]]"
  - "[[concepts/EvidenceAttestationSignedEvalArtifact边界]]"
  - "[[concepts/VerifierPolicyTrustRootRotation边界]]"
  - "[[concepts/EvidenceRetentionAuditPacketLifecycle边界]]"
  - "[[concepts/CrossVerifierPolicyDriftConformanceTest边界]]"
sources:
  - "[[sources/openssf-model-signing-2026]]"
  - "[[sources/sigstore-cosign-custom-components-trust-root-2026]]"
  - "[[sources/openai-api-data-controls-2026]]"
  - "[[sources/azure-foundry-models-data-privacy-2026]]"
  - "[[sources/aws-bedrock-data-protection-2026]]"
  - "[[sources/aws-bedrock-model-invocation-logging-2026]]"
  - "[[sources/google-vertex-ai-data-governance-2026]]"
  - "[[sources/anthropic-api-data-retention-2026]]"
  - "[[sources/anthropic-api-data-residency-2026]]"
  - "[[sources/nist-ai-rmf-1-0-2023]]"
  - "[[sources/anthropic-model-deprecations-2026]]"
  - "[[sources/nist-sp800-92r1-log-management-2023]]"
  - "[[sources/slsa-verification-summary-attestation-v1-2-2026]]"
---

# Multi-provider Governance 边界

Multi-provider governance 是第 7 层产品与组织层的供应商控制面：当同一个 AI 系统同时接 OpenAI、Anthropic、Google、AWS、Azure、本地模型或第三方工具时，它决定哪些请求、数据、用户、风险等级和地域可以发给哪些 provider，并规定 retention、training use、audit、SLA、fallback 和 incident 边界。

一句话：**model routing 选择执行路径；multi-provider governance 决定哪些路径有资格被选择。**

## 主归属

- 主归属：7. 产品与组织层
- 上游输入：请求类型、数据分类、用户/租户、consent/合同、地域要求、风险等级、SLO、成本预算、provider 条款和 eval 结果
- 下游输出：provider allowlist、routing constraint、数据出境规则、logging/retention 策略、fallback/rollback、audit event、vendor review
- 交叉链接：3. 推理与能力层、5. Agent 系统层、6. 评估与可靠性层

## 稳定链路

```text
request / task / data class / risk tier
    -> provider policy matrix
    -> allowed provider / model / tool set
    -> model routing or tool routing decision
    -> provider-specific retention, training-use, region, SLA controls
    -> trace, audit, cost, quality, and drift monitoring
    -> incident, fallback, rollback, and vendor review
```

## 解决的问题

没有这一层，多 provider 系统会把五类决策混在一起：谁最便宜、谁质量最好、谁允许接收这类数据、谁满足地域和保留要求、谁出事故时能回滚。结果是 routing 看似聪明，但可能把 confidential 数据发到不合规 provider，把 private eval 泄漏到日志，把低成本优化压过可靠性要求。

## 核心产物

| 产物 | 作用 |
|---|---|
| Provider registry | 记录 provider、模型、区域、账号、合同、owner、状态和可用功能 |
| Provider policy matrix | 把数据分类、用途、地域、retention、training use 和风险等级映射到允许的 provider |
| Data egress rules | 决定 prompt、文件、tool result、trace、eval 样本能否离开租户或地域 |
| Routing constraints | 给 [[concepts/ModelRoutingMixture边界|model routing]] 一个已过滤的候选集合 |
| Logging and retention policy | 区分 service logs、abuse logs、invocation logs、application state 和 audit logs |
| SLA / SLO dashboard | 按 provider 追踪可用性、错误率、延迟、吞吐、成本和 quota |
| Provider eval suite | 用私有 eval 监控 provider drift、质量退化、安全回归和工具兼容性 |
| Fallback runbook | 规定 provider 故障、条款变化、区域不可用或安全事故时如何切换 |

## 策略矩阵

| 场景 | 默认策略 |
|---|---|
| Public low-risk task | 可用任意已批准 provider；优先成本、延迟和质量 |
| Enterprise confidential data | 只允许具备 no-training、租户隔离、DPA、合适 retention 和审计能力的 provider |
| Regulated personal data / PHI | 需要合同、地域、保留、删除、访问控制和合规能力一起满足 |
| High-impact tool action | provider、model、tool 和人类审批必须同时通过；保留完整 trace |
| Private hold-out eval | 限制 provider、日志和训练用途，防止 eval 泄漏或 benchmark contamination |
| Cost-sensitive low-risk traffic | 只有私有 eval 证明质量合格时，才允许路由到便宜模型或 provider |

## 与相邻概念区别

- 与 [[concepts/ModelRoutingMixture边界]]：routing 是第 3 层运行时选择；multi-provider governance 是第 7 层资格约束。
- 与 [[concepts/ProductionContractCompatibilityTest边界]]：provider governance 判断 provider/model 是否有资格进入候选集；compatibility test 判断具体候选是否满足产品契约。
- 与 [[concepts/EvidenceAttestationSignedEvalArtifact边界]]：provider governance 决定是否信任某个 provider/model/hub；attestation 规定要验证或保存哪些签名、bundle、trust root、model digest 和供应商声明。
- 与 [[concepts/VerifierPolicyTrustRootRotation边界]]：provider governance 决定哪些供应商和 model hub 可进入候选集；verifier policy 规定供应商导出的 evidence bundle、root、issuer 和 signer 如何通过验证及轮换。
- 与 [[concepts/CrossVerifierPolicyDriftConformanceTest边界]]：provider governance 判断哪些 verifier/provider 可被信任；cross-verifier test 检查 delegated VSA verifier、CI、release gate 和 admission 是否产生一致验收结果。
- 与 [[concepts/EvidenceRetentionAuditPacketLifecycle边界]]：provider governance 规定 provider 日志、retention、region、fallback 和 audit 边界；evidence retention 把这些 provider policy、证据包和事故记录长期保存并支持重验。
- 与 [[concepts/DataRightsPrivacyConsent边界]]：data rights 定义数据用途是否允许；multi-provider governance 把用途映射到 provider、region、subprocessor 和 contract。
- 与 [[concepts/ToolRiskPermissioning边界]]：tool permissioning 管工具动作；multi-provider governance 管外部模型、工具供应商和处理方。
- 与 [[concepts/AgentIdentityDelegation边界]]：agent identity / delegation 说明请求代表谁和哪个 agent；multi-provider governance 根据这个主体和数据范围判断 provider 是否可用。
- 与 [[concepts/AISafetyOpsGovernance边界]]：AI safety ops 是整体风险运行系统；multi-provider governance 是其中面向 provider/vendor 的控制面。
- 与 [[concepts/AIIncidentResponsePostmortem边界]]：provider outage、条款变化、数据处理异常或 SLA 失败会触发 incident response，并反哺 provider policy、fallback 和 vendor review。
- 与 [[concepts/Serving成本延迟边界]]：serving 追踪成本和延迟；multi-provider governance 决定何时成本优化不能覆盖数据、合规和可靠性边界。
- 与 [[concepts/ModelReleaseRollbackGate边界]]：provider/model 的新增、替换、弃用、region 迁移和 fallback 演练都要通过 release / rollback gate。

## 评估方式

- Policy coverage：每类数据、用途、用户和风险等级是否都有明确 provider 策略。
- Unauthorized provider usage：请求是否被发送到未批准 provider、model、region 或工具。
- Data residency violation：实际 inference/storage region 是否违反 policy。
- Retention and training-use compliance：日志、应用状态、训练用途和删除策略是否符合承诺。
- Trace completeness：能否重建每次 provider 选择、输入数据类别、policy decision 和结果。
- Fallback success：provider 故障、quota 限制或条款变化时是否能安全降级或切换。
- Provider drift：质量、安全、延迟、成本和输出格式变化是否被私有 eval 捕捉。
- Vendor review cadence：DPA、subprocessor、model card、status、incident 和 pricing 是否定期复审。

## 过时风险

- Provider 条款、默认保留、ZDR 资格、可用区域、模型名和价格会快速变化；source page 必须带日期。
- 平台可能新增托管 memory、agent、tool、batch 或 grounding 功能；每个新功能都可能带来新的应用状态和日志路径。
- 低成本 routing 会诱导系统忽略数据边界；治理规则必须先于 cost optimizer 执行。
- 多 provider 代理层、转发站和灰色 API 会绕过官方控制面，必须进入 vendor/security review。

## 一句话归类

Multi-provider governance 主属第 7 层，是多模型、多云和多工具供应商进入真实产品前的 provider/vendor 控制面；它约束第 3 层 model routing、第 5 层 tool use、第 6 层 eval/monitoring，并把事件反哺第 7 层 governance 和第 8 层自我改进。

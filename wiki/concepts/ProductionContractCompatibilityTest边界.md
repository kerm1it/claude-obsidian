---
address: c-000426
type: concept
title: "Production Contract / Compatibility Test 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - production-contract
  - compatibility-test
  - release-gate
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/ModelReleaseRollbackGate边界]]"
  - "[[concepts/EvalResultInterpretationDecisionThreshold边界]]"
  - "[[concepts/JudgeDriftGraderObservability边界]]"
  - "[[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]"
  - "[[concepts/MultiProviderGovernance边界]]"
  - "[[concepts/EvidenceAttestationSignedEvalArtifact边界]]"
  - "[[concepts/AISafetyOpsGovernance边界]]"
  - "[[concepts/CrossVerifierPolicyDriftConformanceTest边界]]"
sources:
  - "[[sources/slsa-provenance-v1-2-2026]]"
  - "[[sources/sigstore-cosign-verifying-attestations-2026]]"
  - "[[sources/openssf-model-signing-2026]]"
  - "[[sources/test-before-you-deploy-llm-supply-chain-2026]]"
  - "[[sources/openai-model-deprecations-2026]]"
  - "[[sources/openai-model-release-notes-2026]]"
  - "[[sources/anthropic-model-deprecations-2026]]"
  - "[[sources/google-cloud-deploy-automation-2026]]"
  - "[[sources/attesting-llm-pipelines-release-claims-2026]]"
  - "[[sources/together-ai-deprecations-2026]]"
  - "[[sources/open-policy-agent-policy-testing-2026]]"
---

# Production Contract / Compatibility Test 边界

Production contract / compatibility test 是第 6 层评估与可靠性层的可测试产品契约边界：它把产品对模型行为、格式、工具、安全、成本、延迟、数据处理和用户体验的稳定要求写成版本化 contract，并在 provider/model/prompt/router/skill 更新前用 compatibility tests 验证。

一句话：**production contract 写“这个 AI 产品必须一直满足什么”，compatibility test 验证“新模型或新供应链 artifact 是否仍满足”。**

## 主归属

- 主归属：6. 评估与可靠性层
- 上游输入：产品承诺、用户任务、风险分类、历史失败、release notes、model deprecation、provider policy、SLO、data rights
- 下游输出：compatibility pass/fail/limited decision、migration risk、contract violation、fallback/rollback signal、release gate evidence
- 产品接口：7. 产品与组织层
- 推理接口：3. 推理与能力层
- Agent 接口：5. Agent 系统层

## 稳定链路

```text
product promise + risk tier + model/provider dependency inventory
    -> production contract: required behavior, forbidden behavior, schemas, tools, data handling, SLO, safety, tone, refusal, cost
    -> compatibility suite: golden tasks, schema tests, metamorphic tests, trace checks, canary prompts, shadow traffic, adversarial cases
    -> run against current baseline and candidate model/provider/prompt/router/skill
    -> interpret results with thresholds, uncertainty, guardrails, and slices
    -> gate: admit, limit, reject, canary, route around, fallback, migrate, or rollback
    -> update contract only through explicit product/risk review
```

## Contract 内容

| Contract 面 | 典型测试 | 失败后动作 |
|---|---|---|
| Output schema | JSON schema、字段存在、类型、枚举、空值 | block release、修 prompt/tool schema |
| Task behavior | golden tasks、reference outputs、state checks | hold/canary、补 eval 或换模型 |
| Tool behavior | tool choice、参数提取、权限、side-effect boundary | disable tool、收紧权限、rollback |
| Safety / refusal | red-team、policy examples、high-impact action tests | hard block、human review |
| Data handling | tenant isolation、PII redaction、vendor eligibility | route away、provider exclusion |
| Style / personality | product voice、tone、verbosity、locale | limited release、prompt adjustment |
| Cost / latency | TTFT、TPOT、cost/success、retry rate | router fallback、serving optimization |
| Compatibility drift | canary prompts、shadow traffic、nightly contract suite | alert、pin snapshot、rollback |

## 与相邻概念区别

- 与 [[concepts/ModelReleaseRollbackGate边界]]：release gate 执行发布、灰度、回滚；production contract 提供 gate 要验证的可测试行为契约。
- 与 [[concepts/EvalResultInterpretationDecisionThreshold边界]]：decision threshold 解释结果是否足以通过；production contract 定义哪些行为必须被测。
- 与 [[concepts/JudgeDriftGraderObservability边界]]：如果 contract suite 使用 LLM judge，本页消费 judge health signal，防止兼容性报告建立在漂移评分器上。
- 与 [[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]：eval lifecycle 治理测试资产；production contract 把产品承诺映射成这些测试资产。
- 与 [[concepts/MultiProviderGovernance边界]]：multi-provider governance 决定 provider 是否有资格；compatibility test 验证合格 provider 的具体模型/版本是否满足产品契约。
- 与 [[concepts/EvidenceAttestationSignedEvalArtifact边界]]：production contract 验证产品行为是否兼容；attestation 验证 compatibility report、被测 artifact、测试配置和签名身份是否可被信任。
- 与 [[concepts/CrossVerifierPolicyDriftConformanceTest边界]]：production contract 测新模型/provider 是否保持产品行为；cross-verifier test 测 policy verifier 本身在 CI、gate 和 admission 中是否一致。
- 与 provider model spec：provider spec 描述模型应如何行为；production contract 描述你的产品依赖哪些行为，范围更窄、更产品化、更可测试。
- 与 API contract：API contract 只约束接口；production contract 还约束语义、拒答、安全、工具调用、trace、成本和用户体验。

## 工程实践

1. 把 contract 从 prompt 中抽离：prompt 是实现，contract 是验收标准。
2. 每个 contract clause 都要有 owner、risk tier、test cases、threshold、failure action 和 refresh trigger。
3. 维护 model/provider dependency inventory：模型 alias、snapshot、region、provider、tool、skill、prompt、router 都要可追踪。
4. 对 provider release notes、deprecation、silent update 和 model alias 漂移建立监控入口。
5. 新模型迁移前先跑 current baseline vs candidate；差异进入 compatibility report，而不是直接替换。
6. 对高风险 contract 使用 hard block；对低风险风格差异可以 limited release 或 prompt fix。
7. 对长期依赖的模型建立 canary prompt / shadow traffic / nightly suite，检测 provider drift。

## 评估方式

- Contract coverage：关键产品承诺是否都有测试映射。
- Compatibility pass rate：候选模型/版本在 contract suite 上的通过率和关键 guardrail 结果。
- Drift detection latency：provider 或 alias 行为改变到被检测出的时间。
- False compatibility：contract 通过但生产出现关键回归的比例。
- Migration readiness：deprecation deadline 前是否完成替代模型验证和流量迁移。
- Artifact attestation coverage：模型、adapter、dataset、prompt、container、dependency 是否有来源和 release claims。
- Rollback readiness：contract 失败后是否能自动 fallback、route away 或恢复上一个稳定版本。

## 过时风险

- 具体 provider lifecycle、model alias 和 release note 格式会变化；把产品行为写成 contract 并在更新前测试的模式稳定。
- 随着模型更强，兼容性风险会从 schema 和 task accuracy 扩展到人格、工具副作用、推理预算、隐私、数据地域和长期记忆。
- 如果供应商不提供透明版本信息，应用侧更需要 canary、shadow 和 contract diff。

## 一句话归类

Production contract / compatibility test 主属第 6 层，是模型和供应链更新进入第 7 层 release/rollback gate 前的可测试产品契约；它防止“新模型总体更强”掩盖产品关键行为不兼容。

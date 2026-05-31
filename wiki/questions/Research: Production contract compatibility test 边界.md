---
address: c-000427
type: synthesis
title: "Research: Production contract compatibility test 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - research
  - ai
  - compatibility-test
  - release-gate
status: active
related:
  - "[[concepts/ProductionContractCompatibilityTest边界]]"
  - "[[concepts/ModelReleaseRollbackGate边界]]"
  - "[[concepts/EvalResultInterpretationDecisionThreshold边界]]"
sources:
  - "[[sources/test-before-you-deploy-llm-supply-chain-2026]]"
  - "[[sources/openai-model-deprecations-2026]]"
  - "[[sources/openai-model-release-notes-2026]]"
  - "[[sources/anthropic-model-deprecations-2026]]"
  - "[[sources/google-cloud-deploy-automation-2026]]"
  - "[[sources/attesting-llm-pipelines-release-claims-2026]]"
  - "[[sources/together-ai-deprecations-2026]]"
---

# Research: Production contract compatibility test 边界

## Overview

本轮研究把 production contract / compatibility test 归入第 6 层评估与可靠性层。它定义产品依赖模型持续满足的行为契约，并在模型、provider、prompt、router、skill 或供应链 artifact 更新前验证兼容性。

核心结论：**release gate 负责执行上线；production contract 负责告诉 gate 什么叫“仍然兼容”。**

## Key Findings

- “Test Before You Deploy” 将 LLM 托管服务更新视为 supply chain governance，并提出 production contracts、risk-category testing suite 和 compatibility gates 三件套。（Source: [[sources/test-before-you-deploy-llm-supply-chain-2026]]）
- 该论文的探索结果显示，按风险类别做针对性测试能发现总体指标掩盖的回归；同时阈值、非确定性系统和 provider 透明度仍是开放问题。（Source: [[sources/test-before-you-deploy-llm-supply-chain-2026]]）
- OpenAI model release notes 显示 provider 会持续调整模型、响应风格、thinking time、功能入口和退休计划；应用不能把模型行为当成静态依赖。（Source: [[sources/openai-model-release-notes-2026]]）
- OpenAI deprecations 与 Anthropic model deprecations 都把 recommended replacement、retirement date、客户通知和迁移测试变成应用侧治理输入。（Source: [[sources/openai-model-deprecations-2026]]、[[sources/anthropic-model-deprecations-2026]]）
- Google Cloud Deploy automation 提供 staged rollout、canary、retry 和 rollback 的通用执行机制；compatibility test 的结果最终要进入这样的发布执行面。（Source: [[sources/google-cloud-deploy-automation-2026]]）
- Attesting LLM Pipelines 强调第三方 weights、adapters、datasets、packages 和 containers 的 release claims 需要和 artifact 绑定，并通过 promotion gate 验证。（Source: [[sources/attesting-llm-pipelines-release-claims-2026]]）
- Together AI deprecations 文档说明 provider 会用 lifecycle policy 管理 upgrades、redirects 和 scheduled deprecations；多 provider 系统需要把这些生命周期信号纳入 inventory 和 tests。（Source: [[sources/together-ai-deprecations-2026]]）

## Stable Classification

- 主归属：6. 评估与可靠性层
- 上游：产品承诺、风险分类、用户任务、provider lifecycle、release notes、历史失败、data rights、SLO
- 下游：release gate、rollback、provider migration、routing fallback、multi-provider policy、incident prevention
- 交叉链接：7. 产品与组织层负责 owner、迁移 deadline、用户沟通和执行；3. 推理与能力层承接具体模型/provider 更新；5. Agent 系统层承接 tool/skill/harness 兼容性。

## Decision Framework

```text
product behavior promise
    -> production contract clause
    -> test mapping and risk tier
    -> current baseline vs candidate run
    -> threshold and uncertainty interpretation
    -> admit / limit / reject / canary / fallback / rollback
```

## Engineering Practice

- 把 prompt、policy、tool schema、JSON schema、style guide、safety rule 和 SLO 背后的稳定要求写成 contract。
- 每条 contract clause 必须能映射到至少一个测试、一个失败动作和一个 owner。
- provider/model alias 更新前先跑 compatibility suite，不让 overall benchmark 替代产品契约。
- 对 deprecation deadline 建 migration card：usage audit、replacement shortlist、eval suite、contract test、canary、rollback 和用户沟通。
- 对 silent update 风险建立 nightly canary prompts 和 shadow traffic。
- 对 supply-chain artifact 要求 attestation：来源、版本、构建、扫描、lineage 和 release claims。

## Open Questions

- Production contract 如何自动从真实产品事故、用户投诉和 postmortem 中生成或更新，仍需要更多工程实践。
- 对开放式对话和人格/风格契约，如何设置低噪声的兼容性阈值仍不稳定。
- Provider 不提供 snapshot pinning 或详细 release diff 时，应用侧只能通过 canary 和 shadow traffic 推断漂移。

## Sources

- [[sources/test-before-you-deploy-llm-supply-chain-2026]]：production contracts / compatibility gates。
- [[sources/openai-model-deprecations-2026]]：OpenAI API model lifecycle and deprecations。
- [[sources/openai-model-release-notes-2026]]：模型更新和退休沟通。
- [[sources/anthropic-model-deprecations-2026]]：Anthropic Active / Legacy / Deprecated / Retired 生命周期。
- [[sources/google-cloud-deploy-automation-2026]]：canary / retry / rollback 执行机制。
- [[sources/attesting-llm-pipelines-release-claims-2026]]：LLM supply-chain artifact attestation 和 promotion gate。
- [[sources/together-ai-deprecations-2026]]：provider lifecycle policy、redirects、scheduled deprecations。

---
address: c-000401
type: synthesis
title: "Research: Model release rollback gate 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - research
  - ai
  - release-gate
  - rollback
status: developing
related:
  - "[[concepts/ModelReleaseRollbackGate边界]]"
  - "[[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]"
  - "[[concepts/AISafetyOpsGovernance边界]]"
sources:
  - "[[sources/openai-sycophancy-gpt4o-rollback-2025]]"
  - "[[sources/openai-model-deprecations-2026]]"
  - "[[sources/openai-model-release-notes-2026]]"
  - "[[sources/anthropic-model-deprecations-2026]]"
  - "[[sources/google-cloud-deploy-automation-2026]]"
  - "[[sources/test-before-you-deploy-llm-supply-chain-2026]]"
---

# Research: Model release rollback gate 边界

## Overview

Model release / rollback gate 的稳定核心是“AI 变更必须像产品发布一样治理，但比普通软件发布多一层行为、数据、工具和 provider 漂移风险”。它主属第 7 层，因为最终问题是 owner、阈值、上线、例外、回滚、沟通和迁移；第 6 层提供 eval、monitoring、lineage 和 incident evidence。

## Key Findings

- OpenAI 的 GPT-4o sycophancy rollback 说明：离线 eval、A/B test 和专家 spot check 都可能漏掉行为回归；发布流程需要把人格、幻觉、欺骗、可靠性等行为问题变成 launch-blocking concern。（Source: [[sources/openai-sycophancy-gpt4o-rollback-2025]]）
- OpenAI deprecations 与 model release notes 把模型生命周期变成 API/产品兼容性问题：依赖模型的软件必须处理 legacy、deprecation、shutdown、recommended replacement、release note 和 sunset window。（Source: [[sources/openai-model-deprecations-2026]]、[[sources/openai-model-release-notes-2026]]）
- Anthropic model deprecations 明确 Active / Legacy / Deprecated / Retired 状态，并建议在 retirement date 前测试替代模型；这支持 migration gate 和 usage audit。（Source: [[sources/anthropic-model-deprecations-2026]]）
- Google Cloud Deploy automation 提供通用工程模式：canary phase、automatic advancement、retry、repair rollout 和 rollback to most recent successful release。（Source: [[sources/google-cloud-deploy-automation-2026]]）
- LLM supply-chain update governance 论文把 provider-side silent update 视为应用供应链风险，提出 production contracts、risk-category testing suites 和 compatibility gates。（Source: [[sources/test-before-you-deploy-llm-supply-chain-2026]]）

## Stable Classification

- 主归属：7. 产品与组织层
- 上游：model/prompt/router/skill/tool/provider candidate、eval suite、risk tier、lineage、SLO、data rights、deprecation notice、incident history
- 下游：release decision、canary/AB/shadow rollout、rollback plan、migration plan、release notes、audit trail、new regression eval
- 关键连接：第 6 层维护 eval 可信度；第 7 层把 eval 绑定到发布、回滚和迁移；第 8 层只能在 gate 之后接收通过验证的改进。

## Engineering Practice

1. 为每个变更记录 artifact identity、owner、risk tier、blast radius、version/hash 和 rollback owner。
2. 把 eval suite 分成 regression、private hold-out、safety/behavior、tool/data/provider、latency/cost 和 production contract tests。
3. 对高风险变更使用 shadow、internal dogfood、opt-in alpha、canary、A/B、tenant/region ramp。
4. 对 provider alias 和模型更新建立 canary prompts、compatibility gate、snapshot pinning、fallback provider 和 deprecation migration plan。
5. 设置 rollback trigger：eval miss、SLO break、cost spike、投诉、安全告警、data rights violation、provider incident。
6. 回滚或事故后写 postmortem，把失败 case 写入 regression eval 和 release checklist。

## Open Questions

- 托管模型 provider 不总是提供完整版本透明度；应用侧 compatibility gate 只能降低 silent update 风险，不能完全消除。
- 非确定性模型的 release threshold 需要置信区间和 flakiness 预算，否则一次性分数容易误导发布决策。
- 对人格、语气、信任、过度迎合等行为问题，定量 eval 和 qualitative spot check 必须组合；单靠 A/B feedback 会放大短期偏好。

## Sources

- [[sources/openai-sycophancy-gpt4o-rollback-2025]]：行为回归、rollback、launch-blocking behavior issues。
- [[sources/openai-model-deprecations-2026]]：API deprecation、legacy、shutdown、recommended replacement。
- [[sources/openai-model-release-notes-2026]]：模型更新、retirement、sunset、fallback 信息。
- [[sources/anthropic-model-deprecations-2026]]：Active / Legacy / Deprecated / Retired lifecycle 与 migration testing。
- [[sources/google-cloud-deploy-automation-2026]]：canary automation、retry、repair rollout、rollback。
- [[sources/test-before-you-deploy-llm-supply-chain-2026]]：production contracts、risk-category tests、compatibility gates。

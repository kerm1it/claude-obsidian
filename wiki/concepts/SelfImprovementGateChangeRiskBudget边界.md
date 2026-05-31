---
address: c-000567
type: concept
title: "Self-Improvement Gate / Change-Risk Budget 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - self-improvement
  - change-gate
  - governance
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/Dream与SelfImprovement工程原语]]"
  - "[[concepts/自我改进AI循环]]"
  - "[[concepts/ModelReleaseRollbackGate边界]]"
  - "[[concepts/EvalResultInterpretationDecisionThreshold边界]]"
  - "[[concepts/RewardHackingEvalOverfitting边界]]"
  - "[[concepts/DataFlywheelFeedbackLoop边界]]"
  - "[[concepts/ProductFeedbackClosureActionability边界]]"
  - "[[concepts/DatasetLineageProvenanceGraph边界]]"
  - "[[concepts/SyntheticDataGovernance边界]]"
  - "[[concepts/AISafetyOpsGovernance边界]]"
  - "[[concepts/MemorySkillGovernanceDrift边界]]"
sources:
  - "[[sources/automated-self-testing-quality-gate-llm-applications-2026]]"
  - "[[sources/moss-self-evolution-source-rewriting-2026]]"
  - "[[sources/autogenesis-self-evolving-agent-protocol-2026]]"
  - "[[sources/darwin-godel-machine-self-improving-agents-2025]]"
  - "[[sources/nist-ai-rmf-core-manage-change-management-2023]]"
  - "[[sources/google-mlops-continuous-delivery-2026]]"
  - "[[sources/google-sre-error-budget-policy-2018]]"
  - "[[sources/sia-self-improving-ai-2026]]"
  - "[[sources/seal-self-adapting-language-models-2025]]"
  - "[[sources/memmorph-tool-hijacking-memory-poisoning-2026]]"
  - "[[sources/aws-genai-production-feedback-loops-2026]]"
  - "[[sources/adaptive-data-flywheel-mape-ai-agent-improvement-2025]]"
---

# Self-Improvement Gate / Change-Risk Budget 边界

Self-improvement gate / change-risk budget 是第 8 层自我改进与前沿层的准入边界：它把 dream、feedback loop、agent self-edit、harness update、eval update 或 weight update 生成的 proposed diff，按目标层级、影响面、可逆性、证据质量和预算消耗，转成自动应用、沙箱/灰度、人工审查、hold、rollback 或 reject 的决策。

一句话：**self-improvement 可以提出改动；change gate 决定这次改动有没有资格影响系统。**

## 主归属

- 主归属：8. 自我改进与前沿层
- 质量输入：6. 评估与可靠性层
- 组织执行：7. 产品与组织层
- 上游输入：trace、incident、eval failure、用户反馈、dream output、agent proposal、model optimization candidate、lineage
- 下游输出：applied diff、sandbox trial、canary plan、human review package、rollback、rejected proposal、budget burn record
- 反哺层级：2. 模型构建层、4. 上下文与知识层、5. Agent 系统层、6. 评估与可靠性层、7. 产品与组织层

## 稳定链路

```text
trace / outcome / failure / feedback
    -> improvement proposal or diff
    -> target classification: memory, prompt/context, skill, tool, harness, eval, router, data, training, weights
    -> risk scoring: blast radius, reversibility, evidence quality, rights, security, eval touch, user impact
    -> change-risk budget check
    -> gate package: tests, evals, lineage, rollback, owner, expiry
    -> action: auto-apply low-risk, canary/sandbox medium-risk, human approval high-risk, reject hard-stop
    -> production monitoring and budget burn update
    -> post-action review and rule update
```

## 风险分层

| 风险层 | 典型改动 | 默认动作 |
|---|---|---|
| L1 低风险外部知识 | 文档链接、memory 去重、低影响 prompt copy、非生产 skill metadata | 可自动应用，但必须有 provenance、diff、回滚和抽样 eval |
| L2 中风险运行时 | prompt/context policy、RAG index、skill body、tool schema、router policy、harness config | 沙箱、回归 eval、权限检查、canary 或人工复核 |
| L3 高风险控制面 | eval、grader、reward、logging、release gate、permission policy、monitor threshold | 默认人工审查；因为它们能改变 gate 本身 |
| L4 高风险模型面 | SFT/RFT、distillation、adapter、weights、training data admission | hold-out eval、lineage、release gate、rollback/replace plan 和人工批准 |
| Hard stop | 权限扩大、删除/隐私冲突、绕过 eval、污染 hold-out、不可回滚高影响改动 | reject 或进入 safety ops / incident path |

## 与相邻概念区别

- 与 [[concepts/Dream与SelfImprovement工程原语]]：dream/self-improvement 说明改动从哪里来；本页说明改动如何被准入、预算化、灰度和回滚。
- 与 [[concepts/ModelReleaseRollbackGate边界]]：release gate 管一般 AI artifact 进入真实流量；self-improvement gate 是 release gate 的前置和特化，重点处理“系统自己提出的改动”。
- 与 [[concepts/EvalResultInterpretationDecisionThreshold边界]]：decision threshold 把 eval 分数变成 pass/fail/gray-zone；本页把多个阈值、lineage、权限、回滚和预算组合成 self-improvement action。
- 与 [[concepts/RewardHackingEvalOverfitting边界]]：reward hacking 是本页必须防的核心失效模式，尤其是 self-improvement 修改 eval、reward、logs 或 gate policy 时。
- 与 [[concepts/DataFlywheelFeedbackLoop边界]]：data flywheel 提供真实反馈；self-improvement gate 判断反馈生成的 diff 能不能落地。
- 与 [[concepts/ProductFeedbackClosureActionability边界]]：feedback closure 产生可行动反馈和 closure evidence；当这些行动被自动转成 diff 时，本页决定能否自动应用、灰度、人工审查或拒绝。
- 与 [[concepts/SyntheticDataGovernance边界]]：self-improvement 可提出 synthetic cases 或 teacher outputs；synthetic data governance 先判断样本能否进入 eval/training，再由本页决定改动能否应用。
- 与 [[concepts/AISafetyOpsGovernance边界]]：safety ops 定义风险运行系统；本页是第 8 层改动进入该系统和生产系统的 change admission boundary。

## 工程规则

1. 每个 self-improvement proposal 必须是 diff，不是直接改写事实源或 gate 配置。
2. 每个 diff 必须标 target layer：2/4/5/6/7/8，以及 artifact identity、owner、lineage 和 rollback path。
3. L1 可自动应用的前提是影响面小、可逆、来源清楚、不会触碰 eval/reward/permission/gate。
4. 修改 eval、judge、reward、日志、policy、permission、release gate 的 diff 属于控制面改动，默认更严格。
5. 修改 skill/tool/harness/router 的 diff 必须跑 regression、security、permission 和 production contract checks。
6. 修改 training data、adapter、fine-tune 或 weights 必须经过 hold-out、污染检查、model release gate 和人工批准。
7. 使用 change-risk budget：当 rollback、incident、false promote、gate miss 或 override debt 升高时，自动改动额度下降。
8. Gate 结果必须写入 audit packet：proposal、证据、decision、预算消耗、owner、监控、过期时间和复盘。
9. 对 memory/skill diff 先过 [[concepts/MemorySkillGovernanceDrift边界|memory / skill governance drift]]：检查 stale、poison、permission drift、routing drift、dependency/API drift、owner 和 retirement path。

## 评估方式

- Net improvement：应用后真实任务成功率、人工接管率、成本/成功、用户结果是否改善。
- False promote：gate 放行但后来导致回滚、事故、用户影响或安全破线的比例。
- False block：gate 阻止但后续人工确认低风险且有价值的比例。
- Budget burn：单位时间内 self-improvement 引起的 rollback、incident、override、monitor breach 和 gate debt。
- Evidence completeness：proposal 是否有 lineage、eval、权限、rollback、owner、expiry。
- Control-plane safety：eval/reward/log/policy/gate 改动是否被隔离审查，是否存在 gate tampering。
- Regression escape：self-improvement 后是否在未覆盖 slice、长任务、工具路径或 provider path 上退化。
- Rollback readiness：自动应用或 canary 后能否在目标时间内回退。

## 过时风险

- “self-improvement gate”这个名字可能被平台叫作 agent update policy、auto-patch review、continuous learning gate 或 managed evolution，但 proposed diff -> evidence -> risk budget -> staged action -> monitor -> rollback 的结构稳定。
- 更强模型会增加 proposal 质量，也会增加对 gate 的攻击面：它更懂得如何优化指标、绕过权限或修改监督机制。
- 权重级自我改进若成熟，会把更多 L4 改动推向自动化，但仍需要 hold-out、lineage、rollback、human accountability 和 hard-stop rule。

## 一句话归类

Self-improvement gate / change-risk budget 主属第 8 层，是自我改进 diff 反哺第 2/4/5/6/7 层前的准入、预算和回滚边界；它防止“会提出改动”误变成“可以随便改系统”。

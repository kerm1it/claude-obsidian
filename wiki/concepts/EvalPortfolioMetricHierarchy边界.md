---
address: c-000471
type: concept
title: "Eval Portfolio / Metric Hierarchy 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - evals
  - metrics
  - release-governance
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]"
  - "[[concepts/EvalResultInterpretationDecisionThreshold边界]]"
  - "[[concepts/EvalUncertaintyCommunicationReleaseCard边界]]"
  - "[[concepts/ModelReleaseRollbackGate边界]]"
  - "[[concepts/PostReleaseEvalDrift边界]]"
  - "[[concepts/EvidenceFreshnessStaleProof边界]]"
  - "[[concepts/MonitorOwnershipEscalationLadder边界]]"
  - "[[concepts/MetricConflictResolution边界]]"
  - "[[concepts/DashboardCalibrationGovernanceMetricQuality边界]]"
  - "[[concepts/RewardHackingEvalOverfitting边界]]"
sources:
  - "[[sources/google-sre-embracing-risk-2016]]"
  - "[[sources/google-sre-monitoring-distributed-systems-2016]]"
  - "[[sources/nist-sp800-55-measurement-guide-2024]]"
  - "[[sources/nist-ai-rmf-playbook-monitoring-responsibility-2026]]"
  - "[[sources/openai-evaluation-best-practices-2026]]"
  - "[[sources/openai-evals-framework-2026]]"
  - "[[sources/openai-simple-evals-2026]]"
  - "[[sources/openai-evals-business-framework-2025]]"
  - "[[sources/helm-holistic-evaluation-2022]]"
  - "[[sources/google-ml-test-score-2016]]"
  - "[[sources/safety-case-maintenance-slr-2021]]"
  - "[[sources/openai-trustworthy-third-party-evaluations-2026]]"
---

# Eval Portfolio / Metric Hierarchy 边界

Eval portfolio / metric hierarchy 是第 6 层评估与可靠性层的证据组合边界：它把 public benchmark、private hold-out、regression eval、production contract、red-team、LLM judge、人类评审、online eval、business metric、SLO 和 post-release monitor 组织成分层指标组合，说明哪些指标能拦发布，哪些只能诊断，哪些需要进入 release card 或 safety case。

一句话：**一个 AI 系统不应该用一个总分决策；它需要一组有优先级、作用域、owner 和行动规则的 eval portfolio。**

## 主归属

- 主归属：6. 评估与可靠性层
- 组织接口：7. 产品与组织层
- 上游输入：产品目标、risk tier、artifact identity、eval datasets、benchmarks、contract tests、red-team cases、judge/human labels、online outcomes、SLO
- 下游输出：metric hierarchy、evidence matrix、gate package、release card inputs、safety case evidence map、refresh / retire plan
- 反馈接口：[[concepts/PostReleaseEvalDrift边界]]

## 稳定链路

```text
decision to control: release, rollback, route, train, restrict, refresh
    -> evidence inventory: benchmarks, hold-out, regression, red-team, contract, judge, human, online, SLO
    -> metric roles: hard stop, guardrail, primary, slice, diagnostic, exploratory
    -> hierarchy: precedence, conflict resolution, owner, action, freshness, trust tier
    -> run portfolio on candidate and baseline
    -> interpret with thresholds, uncertainty, and validity limits
    -> produce release card, gate decision, safety case evidence, or refresh task
```

## 指标角色

| 角色 | 回答的问题 | 决策权重 |
|---|---|---|
| Hard stop | 是否触发法律、严重安全、不可容忍风险或 critical contract breach？ | 一票否决 |
| Guardrail | 候选是否伤害安全、隐私、公平、拒答、tool permission、成本或延迟底线？ | 通常阻断或灰区 |
| Primary metric | 核心任务是否比 baseline 更好？ | 支持发布或选择 |
| Slice metric | 关键语言、用户、工具路径、风险类别是否稳定？ | 限制范围或补样本 |
| Regression metric | 已知失败是否不复发？ | 阻断回归 |
| Online / business metric | 线上真实 outcome 是否同向？ | 校准或推广 |
| Diagnostic metric | 为什么失败、该改哪里？ | 不直接放行 |
| Exploratory metric | 新能力或新风险的早期信号 | 进入研究队列 |

## 与相邻概念区别

- 与 [[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]：benchmark governance 管 eval 资产的来源、split、版本、泄漏和退役；本页把多种 eval 资产组织成可决策的组合。
- 与 [[concepts/EvalResultInterpretationDecisionThreshold边界]]：threshold 解释某个指标是否过线；本页先定义哪些指标存在、谁优先、冲突时谁说了算。
- 与 [[concepts/EvalUncertaintyCommunicationReleaseCard边界]]：release card 对外表达一次变更的证据；eval portfolio 是卡片背后的指标组合和证据矩阵。
- 与 [[concepts/ModelReleaseRollbackGate边界]]：release gate 执行动作；eval portfolio 提供 gate 消费的分层证据。
- 与 [[concepts/PostReleaseEvalDrift边界]]：portfolio 定义证据组合；post-release drift 监控这些证据是否 stale、饱和或失去线上相关性。
- 与 [[concepts/EvidenceFreshnessStaleProof边界]]：portfolio 说明哪些证据可用于决策；freshness/stale proof 说明这些证据当前是否仍可用。
- 与 [[concepts/MonitorOwnershipEscalationLadder边界]]：portfolio 定义指标优先级和 action ladder；monitor ownership 给每类指标失败绑定 owner、SLA 和升级路径。
- 与 [[concepts/MetricConflictResolution边界]]：portfolio 定义指标角色；metric conflict resolution 定义 hard stop、guardrail、primary、slice、online 和 business metric 冲突时谁优先。
- 与 [[concepts/DashboardCalibrationGovernanceMetricQuality边界]]：portfolio 定义指标角色、优先级和证据组合；dashboard calibration 检查这些指标进入看板后是否仍有清楚定义、数据血缘、行动精度、漏报审查和退役规则。

## 工程实践

1. 先列 decision inventory：发布、回滚、路由、训练、provider 切换、scope restriction、human escalation。
2. 每个 decision 绑定一个 eval portfolio，而不是全局总分。
3. 把指标分成 hard stop、guardrail、primary、slice、regression、online、diagnostic、exploratory。
4. Public benchmark 只做通用能力参照；private hold-out 和产品 regression 才进入 release gate。
5. Red-team、安全、隐私、tool permission 和不可容忍风险默认优先级高于平均质量提升。
6. 不用加权平均掩盖冲突；冲突要进入 release card 的 limitation / gray zone / exception。
7. 给每个指标记录 owner、cadence、freshness、trust tier、staleness trigger、cost 和 action ladder。
8. 定期清理饱和、漂移、低相关、被污染或不再影响决策的指标。

## 评估方式

- Decision coverage：关键发布、回滚、路由、训练和风险决策是否都有对应证据。
- False pass / false fail：portfolio 是否减少坏候选放行和好候选误杀。
- Conflict handling：primary 提升但 guardrail 下降时是否有明确规则。
- Portfolio freshness：指标是否随产品、用户分布、模型、judge 和 provider 变化刷新。
- Actionability：每个指标失败后是否知道 owner 和下一步动作。
- Cost / latency of evaluation：组合是否能在 CI、pre-release、canary、post-release 节奏中运行。
- Production correlation：指标组合是否比单一指标更能预测线上 outcome。

## 过时风险

- 具体 benchmark、grader 和在线指标会快速变化，但“多证据组合 + 指标优先级 + 冲突规则 + action owner”稳定。
- 模型越强，public benchmark 越容易饱和，portfolio 要把重心放到 private product eval、tool trace、safety、online correlation 和 post-release drift。
- 如果组织只追一个总分，reward hacking、eval overfitting 和严重 slice regression 会被平均值掩盖。

## 一句话归类

Eval portfolio / metric hierarchy 主属第 6 层，是把多种 eval 和指标组织成可决策证据组合的边界；它不新增顶层，而是让第 6 层质量门能稳定服务第 7 层发布、回滚、治理和产品迭代。

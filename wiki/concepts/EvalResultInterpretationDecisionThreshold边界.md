---
address: c-000417
type: concept
title: "Eval Result Interpretation / Decision Threshold 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - evals
  - decision-threshold
  - reliability
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]"
  - "[[concepts/LLMJudgeAIFeedbackCalibration边界]]"
  - "[[concepts/JudgeDriftGraderObservability边界]]"
  - "[[concepts/EvalPortfolioMetricHierarchy边界]]"
  - "[[concepts/MetricConflictResolution边界]]"
  - "[[concepts/DashboardCalibrationGovernanceMetricQuality边界]]"
  - "[[concepts/EvalUncertaintyCommunicationReleaseCard边界]]"
  - "[[concepts/OfflineOnlineEvalCorrelation边界]]"
  - "[[concepts/ModelReleaseRollbackGate边界]]"
  - "[[concepts/ProductionContractCompatibilityTest边界]]"
  - "[[concepts/AISafetyOpsGovernance边界]]"
  - "[[concepts/IntolerableRiskThresholdStopRule边界]]"
  - "[[concepts/RewardHackingEvalOverfitting边界]]"
  - "[[concepts/DataQualityLabelQuality边界]]"
  - "[[concepts/SelfImprovementGateChangeRiskBudget边界]]"
sources:
  - "[[sources/google-sre-embracing-risk-2016]]"
  - "[[sources/responsible-ai-tensions-tradeoffs-2023]]"
  - "[[sources/openai-evaluation-best-practices-2026]]"
  - "[[sources/openai-evals-business-framework-2025]]"
  - "[[sources/anthropic-demystifying-evals-agents-2026-05-26]]"
  - "[[sources/openai-trustworthy-third-party-evaluations-2026]]"
  - "[[sources/google-sre-service-level-objectives-2016]]"
  - "[[sources/google-sre-error-budget-policy-2018]]"
  - "[[sources/google-sre-alerting-on-slos-2018]]"
  - "[[sources/nist-sp800-55-measurement-guide-2024]]"
  - "[[sources/kohavi-controlled-experiments-web-2009]]"
  - "[[sources/chatbot-arena-human-preference-2024]]"
  - "[[sources/anytime-valid-confidence-sequences-ab-testing-2023]]"
  - "[[sources/betterbench-benchmark-quality-2024]]"
  - "[[sources/adding-error-bars-evals-2024]]"
  - "[[sources/automated-self-testing-quality-gate-llm-applications-2026]]"
---

# Eval Result Interpretation / Decision Threshold 边界

Eval result interpretation / decision threshold 是第 6 层评估与可靠性层的证据解释边界：它把 eval score、置信区间、方差、slice regression、成本/延迟、安全信号和风险容忍度，转成发布、回滚、继续实验、人工复核或拒绝的决策规则。

一句话：**eval 分数不是决策；decision threshold 把分数变成可执行质量门。**

## 主归属

- 主归属：6. 评估与可靠性层
- 上游输入：eval objective、dataset、grader、baseline、candidate artifact、uncertainty、risk tier、SLO、business objective
- 下游输出：pass/fail/investigate/escalate/canary/rollback decision、threshold record、exception、owner、next eval gap
- 产品接口：7. 产品与组织层
- 模型接口：2. 模型构建层
- Agent 接口：5. Agent 系统层

## 稳定链路

```text
decision to control: release / rollback / route / train / self-improve
    -> metric family: primary metric, guardrails, slices, cost, latency, safety
    -> baseline and minimum meaningful effect or non-regression margin
    -> sampling plan: dataset size, repeated trials, stratification, online/offline split
    -> uncertainty: confidence interval, bootstrap, confidence sequence, flakiness, judge disagreement
    -> interpretation: practical significance + statistical evidence + safety/risk tolerance
    -> decision band: pass, fail, gray-zone investigate, human escalation, canary, rollback
    -> record threshold, owner, exception path, rationale, and production correlation
    -> refresh thresholds when product distribution, model behavior, grader, or risk context changes
```

## 决策阈值类型

| 阈值类型 | 控制什么 | 典型误区 |
|---|---|---|
| Baseline delta | 候选是否优于当前版本 | 只看绝对分，不和当前生产版本比较 |
| Non-regression margin | 迁移、降成本、换 provider 时可接受损失 | 把小幅损失当成无害，但没有 slice 检查 |
| Guardrail threshold | 安全、隐私、权限、拒答、幻觉、延迟、成本 | 平均质量提升掩盖高风险指标破线 |
| Slice threshold | 长尾用户、语言、任务类型、工具路径 | 总分过线但关键分布失败 |
| Confidence / uncertainty band | 区分真实改善和噪声 | 分数微升就发布，忽略区间重叠和 flakiness |
| Error budget / SLO | 真实服务质量和发布速度的平衡 | eval 过线但 production SLO 已经透支 |
| Escalation threshold | 触发人工复核、专家评审、canary 或 rollback | 高风险灰区被自动放行 |

## 与相邻概念区别

- 与 [[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]：eval dataset lifecycle 管测试资产；本页解释测试结果如何变成决策。
- 与 [[concepts/LLMJudgeAIFeedbackCalibration边界]]：LLM judge calibration 证明评分器能不能测；本页决定测量结果如何过线、不过线或进入灰区。
- 与 [[concepts/JudgeDriftGraderObservability边界]]：grader observability 判断当前分数是否仍来自健康评分器；judge health 异常时，本页阈值应冻结或进入人工灰区。
- 与 [[concepts/EvalPortfolioMetricHierarchy边界]]：metric hierarchy 定义哪些指标是 hard stop、guardrail、primary 或 diagnostic；本页解释每个指标是否过线以及组合后该怎么行动。
- 与 [[concepts/MetricConflictResolution边界]]：本页解释单个指标或指标族是否过线；metric conflict resolution 处理多个过线/破线结果之间的优先级和升级。
- 与 [[concepts/DashboardCalibrationGovernanceMetricQuality边界]]：本页把一个指标解释成阈值决策；dashboard calibration 验证 dashboard 上多个指标的分子、分母、窗口、滞后、行动后效果和误报/漏报是否可靠。
- 与 [[concepts/EvalUncertaintyCommunicationReleaseCard边界]]：本页把 score 和 uncertainty 解释成决策阈值；release card 把解释结果、局限、owner 和监控计划打包给第 7 层审查。
- 与 [[concepts/OfflineOnlineEvalCorrelation边界]]：本页解释一次分数是否足以行动；offline/online correlation 追踪这些阈值长期是否预测真实 outcome。
- 与 [[concepts/ModelReleaseRollbackGate边界]]：release gate 是第 7 层执行点；本页提供 gate 消费的阈值、证据解释和不确定性规则。
- 与 [[concepts/ProductionContractCompatibilityTest边界]]：production contract 定义要测什么；本页决定测出来的结果是否足以通过、失败或进入灰区。
- 与 [[concepts/AISafetyOpsGovernance边界]]：safety ops 定义风险 owner 和组织风险容忍度；本页把风险容忍度落到具体 eval threshold。
- 与 [[concepts/IntolerableRiskThresholdStopRule边界]]：本页处理一般 pass/fail/gray-zone；intolerable risk threshold 处理不能被平均质量或商业收益抵消的 hard stop。
- 与 [[concepts/RewardHackingEvalOverfitting边界]]：reward hacking 是阈值被优化压力钻空子的失效模式；本页要求 hold-out、slice、uncertainty 和生产相关性防止过拟合。
- 与 [[concepts/SelfImprovementGateChangeRiskBudget边界]]：本页解释 eval evidence 是否支持 pass/fail/gray-zone；self-improvement gate 把该解释与 target layer、rollback、权限和 risk budget 组合成 self-improvement action。
- 与 A/B testing：线上实验验证真实用户因果影响；本页同时覆盖离线 eval、agent eval、benchmark、canary 和线上实验的解释规则。

## 工程实践

1. 先写 decision，再选 metric：每个 eval 必须说明控制发布、路由、训练、回滚还是调查。
2. 把指标分成 primary、guardrail 和 diagnostic；只有 primary 用来判定主效果，guardrail 负责否决，diagnostic 负责定位。
3. 所有阈值都和 baseline 比：当前生产版本、上一个 snapshot、人工专家、旧 provider 或 deterministic solver。
4. 对非确定性任务重复运行，报告均值、区间、flakiness、pass@k/pass^k 和 slice 方差。
5. 对小样本或昂贵 agent eval，使用灰区：区间重叠、judge disagreement 或关键 slice 低样本时不自动发布。
6. 对线上实验预先设定样本量、最小可检测效果、停止规则和多重比较处理，避免边看边停造成假阳性。
7. 把安全和权限阈值做成硬 guardrail：总体质量提升不能抵消高影响风险破线。
8. 发布后比较 eval 与 production：投诉、人工接管、事故、留存、成本、延迟和用户满意度是否跟离线指标同向。

## 评估方式

- Decision accuracy：放行的变更是否在生产中改善，阻断的变更是否确实高风险。
- False pass / false fail：阈值导致的误放行和误拒绝比例。
- Confidence width：关键指标的置信区间是否窄到足以支持决策。
- Flakiness rate：同一候选多次 eval 结果是否翻转。
- Slice regression capture：长尾分布、风险路径和高价值任务是否被阈值捕捉。
- Production correlation：离线 eval delta 是否预测线上 KPI、incident、complaint、human override 和 cost/success。
- Exception quality：越过阈值的例外是否有 owner、期限、缓解和复盘。
- Threshold drift：产品分布、model/provider、grader、risk context 变化后阈值是否及时更新。

## 过时风险

- 具体统计工具和实验平台会变化，但 baseline、uncertainty、guardrail、slice、灰区和 production correlation 的解释链路稳定。
- 随着 agent 和多模态任务增多，单一 accuracy 阈值更容易过时；状态检查、trace、成本、权限、安全和用户影响必须进入阈值。
- 强 LLM judge 会降低评分成本，但不会消除不确定性；judge drift 和 human anchor 仍然需要阈值管理。

## 一句话归类

Eval result interpretation / decision threshold 主属第 6 层，是 eval 分数进入 release gate、routing、training、rollback 和 self-improvement 前的证据解释边界；它把“模型得了多少分”变成“现在该做什么”。

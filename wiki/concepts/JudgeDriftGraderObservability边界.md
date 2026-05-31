---
address: c-000430
type: concept
title: "Judge Drift / Grader Observability 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - evals
  - llm-as-judge
  - observability
  - drift
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/LLMJudgeAIFeedbackCalibration边界]]"
  - "[[concepts/EvalResultInterpretationDecisionThreshold边界]]"
  - "[[concepts/EvalUncertaintyCommunicationReleaseCard边界]]"
  - "[[concepts/PostReleaseEvalDrift边界]]"
  - "[[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]"
  - "[[concepts/ProductionContractCompatibilityTest边界]]"
  - "[[concepts/RewardHackingEvalOverfitting边界]]"
sources:
  - "[[sources/judge-verdict-human-agreement-2025]]"
  - "[[sources/closer-look-automatic-evaluation-llms-2023]]"
  - "[[sources/empirical-finetuned-judge-not-general-substitute-2025]]"
  - "[[sources/langsmith-llm-judge-human-feedback-online-evals-2026]]"
  - "[[sources/phoenix-llm-evaluators-observability-2026]]"
  - "[[sources/human-anchored-longitudinal-llm-judge-2026]]"
  - "[[sources/galileo-continuous-llm-judge-calibration-2026]]"
  - "[[sources/aws-prescriptive-genai-drift-detection-2026]]"
---

# Judge Drift / Grader Observability 边界

Judge drift / grader observability 是第 6 层评估与可靠性层的评分器运行监控边界：它把 LLM judge、rubric grader、AI annotator、multi-judge panel 和 hybrid grader stack 当成会随模型版本、prompt、rubric、输入分布、候选模型和人类偏好改变的测量仪器，并持续观测这些测量是否仍可信。

一句话：**judge calibration 证明评分器当时能测；judge observability 证明评分器现在仍然能测。**

## 主归属

- 主归属：6. 评估与可靠性层
- 上游输入：judge model/version/provider、judge prompt、rubric、output schema、candidate outputs、human anchor、production outcome、eval traces
- 下游输出：judge health signal、drift alert、recalibration task、human review queue、threshold freeze、score quarantine、release gate evidence
- 产品接口：7. 产品与组织层
- Agent 接口：5. Agent 系统层
- 自我改进接口：8. 自我改进与前沿层

## 稳定链路

```text
judge inventory: model, provider, version, prompt, rubric, schema, examples, sampling
    -> anchor set: human gold, deterministic checks, bias suites, canaries, production outcomes
    -> scheduled and event-triggered reruns after model/provider/rubric/distribution changes
    -> monitor signals: agreement, calibration, score distribution, flip rate, bias, prompt sensitivity, latency/cost
    -> diagnose drift: judge changed, rubric changed, task distribution changed, candidate mix changed, human preference changed, gaming
    -> action: recalibrate, freeze judge version, add human review, lower trust, adjust threshold, replace judge, quarantine scores
    -> feed corrected evidence back to eval dataset lifecycle, release gate, training, router, or self-improvement
```

## 观测信号

| 信号 | 说明 | 失败含义 |
|---|---|---|
| Human agreement | 与 gold label、expert review、human preference 的一致性 | judge 不再代表目标判断 |
| Calibration | 分数是否预测真实成功率、人工接受率、事故率 | 高分不再等于高质量 |
| Score distribution | 均值、方差、分位数、slice 的漂移 | 评分尺度或输入分布改变 |
| Flip rate | 同一 anchor/canary 重跑后 pass/fail 翻转 | judge 或 prompt 不稳定 |
| Bias suite | position、verbosity、self-preference、leniency、style、model-family bias | judge 被格式或来源诱导 |
| Prompt/rubric sensitivity | 轻微措辞或示例改动导致分数大变 | rubric 不够稳定 |
| Production correlation | judge 分数与投诉、人工覆盖、事故、留存、成功率同向 | 离线评分脱离真实目标 |
| Operational health | latency、cost、timeout、schema failure、provider update | grader 本身成为生产风险 |

## 与相邻概念区别

- 与 [[concepts/LLMJudgeAIFeedbackCalibration边界]]：calibration 是把 judge 校准到 human anchor；本页是上线后持续监控 judge 是否漂移、失真或被优化压力利用。
- 与 [[concepts/EvalResultInterpretationDecisionThreshold边界]]：threshold 解释当前分数能否支持决策；本页先判断这些分数是否来自健康评分器。Judge unhealthy 时，历史阈值不能直接比较。
- 与 [[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]：eval lifecycle 管样本、split、版本、泄漏和退役；本页管评分器、rubric、prompt 和 judge panel 的运行健康。
- 与 [[concepts/ProductionContractCompatibilityTest边界]]：production contract 定义必须测试的产品行为；judge observability 提供 contract suite 中模型评分器是否可信的证据。
- 与 [[concepts/PostReleaseEvalDrift边界]]：judge drift 是发布后 eval drift 的一种输入；当 judge health 异常，release card、threshold 和 online eval 分数都应标记 stale 或 quarantine。
- 与 [[concepts/RewardHackingEvalOverfitting边界]]：reward hacking 是优化压力利用评分器漏洞；本页是检测漏洞、偏差和漂移的监控面。
- 与普通 monitoring：普通监控看模型输出或服务指标；grader observability 监控“测量系统本身”。

## 工程实践

1. 为每个 judge 建 inventory：model/provider/version、prompt hash、rubric version、schema、examples、temperature、candidate order、调用路径和用途。
2. 保留 human anchor / sentinel set：专家 gold、disagreement notes、deterministic checks、bias probes 和高风险 canary samples。
3. 设定重跑触发器：provider release、model alias 改变、prompt/rubric 变更、eval set refresh、候选模型家族变化、生产分布漂移。
4. 记录 judge trace：输入、候选、评分、理由、schema failure、latency、cost、provider response、judge version 和 downstream decision。
5. 建多层 alert：human agreement 下降、score 分布漂移、flip rate 上升、bias suite 破线、production correlation 反向、schema failure 增加。
6. 对 pairwise judge 做 order swap 和 blind labels；对模型家族相近的 judge/candidate 做 self-preference 检测。
7. Judge unhealthy 时冻结 release threshold，触发人工复核或 score quarantine，直到重校准或替换评分器。
8. 把 judge 变更当成 release artifact：需要 diff、owner、eval、rollback 和历史分数可比性说明。

## 评估方式

- Agreement health：accuracy、F1、Cohen's kappa、Krippendorff's alpha、rank correlation、human override rate。
- Calibration health：calibration curve、ECE、Brier score、score bucket outcome rate。
- Drift metrics：PSI/KS test、slice delta、anchor flip rate、canary pass/fail delta、distribution shift。
- Bias metrics：position swap delta、verbosity preference、self-preference lift、style/domain/group bias。
- Reliability metrics：re-run variance、schema error rate、timeout rate、latency/cost trend。
- Decision impact：漂移 alert 是否能提前发现 false pass、false fail、production complaint 或 release rollback。
- Recovery quality：recalibration 后 human agreement、production correlation 和历史 score comparability 是否恢复。

## 过时风险

- 具体 observability 工具会变化，但“评分器是测量仪器，需要持续监控”的模式稳定。
- 更强 judge 会降低人工成本，却不会消除版本漂移、prompt 敏感、输入分布漂移、self-preference 和人类偏好变化。
- 如果 provider 隐式更新 judge model 或 alias，应用侧更需要 canary、anchor set、prompt/rubric hash 和历史 score quarantine。

## 一句话归类

Judge drift / grader observability 主属第 6 层，是 LLM judge 和 grader stack 进入长期 eval、release gate、training feedback 与 self-improvement 前后的持续可信度监控边界；它让“评分器是否还可信”成为可观测系统状态。

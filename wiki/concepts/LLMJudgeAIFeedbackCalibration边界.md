---
address: c-000408
type: concept
title: "LLM-as-Judge / AI Feedback Calibration 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - evals
  - llm-as-judge
  - calibration
  - ai-feedback
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/ReasoningEvalVerifier边界]]"
  - "[[concepts/HumanFeedbackAnnotationOps边界]]"
  - "[[concepts/DataQualityLabelQuality边界]]"
  - "[[concepts/SyntheticDataGovernance边界]]"
  - "[[concepts/RewardHackingEvalOverfitting边界]]"
  - "[[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]"
  - "[[concepts/ModelReleaseRollbackGate边界]]"
  - "[[concepts/JudgeDriftGraderObservability边界]]"
  - "[[concepts/EvalResultInterpretationDecisionThreshold边界]]"
sources:
  - "[[sources/openai-graders-docs-2026]]"
  - "[[sources/anthropic-demystifying-evals-agents-2026-05-26]]"
  - "[[sources/g-eval-2023]]"
  - "[[sources/mt-bench-chatbot-arena-llm-as-judge-2023]]"
  - "[[sources/llm-judge-position-bias-2024]]"
  - "[[sources/llm-judges-alignment-vulnerabilities-2024]]"
  - "[[sources/poll-panel-llm-evaluators-2024]]"
  - "[[sources/llm-evaluators-self-preference-2024]]"
  - "[[sources/alternative-annotator-test-2025]]"
  - "[[sources/judge-verdict-human-agreement-2025]]"
  - "[[sources/closer-look-automatic-evaluation-llms-2023]]"
  - "[[sources/empirical-finetuned-judge-not-general-substitute-2025]]"
  - "[[sources/human-anchored-longitudinal-llm-judge-2026]]"
---

# LLM-as-Judge / AI Feedback Calibration 边界

LLM-as-judge / AI feedback calibration 是第 6 层评估与可靠性层的自动判断校准边界：它把模型评分器、AI 标注员、RLAIF teacher、rubric grader、pairwise comparator 或 multi-judge panel 当成“待评估的测量仪器”，用 human gold、确定性 checks、bias tests、production outcomes 和 lineage 来校准。

一句话：**LLM judge 不是裁判终点，而是一个便宜、灵活、会漂移和有偏的测量仪器。**

## 主归属

- 主归属：6. 评估与可靠性层
- 上游输入：task objective、rubric、candidate outputs、reference answers、human gold labels、production outcomes、judge model/prompt/version
- 下游输出：calibrated score、label、preference、failure reason、uncertainty、human escalation、eval gate signal、training candidate
- 模型接口：2. 模型构建层
- 人类反馈接口：[[concepts/HumanFeedbackAnnotationOps边界]]
- 自我改进接口：8. 自我改进与前沿层

## 稳定链路

```text
task / product / eval objective
    -> decide deterministic, model-based, human, or hybrid grader
    -> write rubric, reference, judge prompt, output schema, and forbidden shortcuts
    -> build human gold / anchor set with adjudication and disagreement notes
    -> run judge with fixed model, prompt, sampling, candidate order, and version
    -> measure agreement, calibration, bias, flakiness, and production correlation
    -> mitigate: order swap, blind labels, multi-judge panel, confidence threshold, human escalation
    -> route score to eval gate, reward/RLAIF, router, self-improvement, or reject
    -> monitor judge drift and periodically recalibrate
```

## Judge 类型

| 类型 | 适用场景 | 主要风险 |
|---|---|---|
| Deterministic / code grader | 有明确答案、schema、状态或测试 | 对合法变体脆弱 |
| Reference-based LLM judge | 有专家参考答案但表达开放 | 参考泄露、语义误判 |
| Rubric score model | 开放任务、客服、研究质量、写作质量 | rubric 模糊、提示敏感、leniency |
| Pairwise comparator | 模型对比、偏好数据、arena | position bias、verbosity bias |
| Multi-judge panel / jury | 高价值或高噪声开放任务 | 成本、相关错误、投票掩盖少数风险 |
| AI annotator / RLAIF teacher | 扩大标注、合成偏好、constitutional feedback | self-confirmation、model-family bias |
| Trained reward model | 大规模训练或 rerank | reward hacking、hold-out 过拟合 |

## 与相邻概念区别

- 与 [[concepts/ReasoningEvalVerifier边界]]：verifier/grader 是更大类；本页专门治理 LLM judge 和 AI feedback 的校准、偏差和替代人工边界。
- 与 [[concepts/HumanFeedbackAnnotationOps边界]]：human feedback 生产 gold、rubric、adjudication；本页用这些人类锚点校准 AI judge。
- 与 [[concepts/SyntheticDataGovernance边界]]：AI feedback 和 LLM-as-judge 产生的标签属于 synthetic evidence，不能自动当成真相。
- 与 [[concepts/RewardHackingEvalOverfitting边界]]：grader hacking 是失效模式；本页提供校准、bias test、hold-out 和 human escalation 防线。
- 与 [[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]：eval lifecycle 管测试资产；本页管评分器本身是否可信、漂移或被优化。
- 与 [[concepts/JudgeDriftGraderObservability边界]]：本页回答 judge 初始能不能测；judge drift / observability 回答它在生产和长期 eval 中是否仍然能测。
- 与 [[concepts/EvalResultInterpretationDecisionThreshold边界]]：本页校准 judge 分数是否可信；decision threshold 决定可信分数如何进入 pass/fail/gray-zone/human escalation。
- 与 [[concepts/ModelReleaseRollbackGate边界]]：release gate 消费 judge 分数；本页证明这些分数能不能作为发布证据。

## 工程实践

1. 能用确定性 grader 就先不用 LLM judge；LLM judge 用在开放、主观、语义、对话质量和 trace 解释任务。
2. 每个 judge 记录 model、version、prompt、rubric、temperature、candidate order、schema、date 和用途。
3. 建 human gold / anchor set：专家或多标注员标注，保留 disagreement 和 adjudication。
4. 用多指标校准：accuracy/F1、Cohen's kappa、Spearman/Kendall、calibration curve、flakiness、bias suite、production correlation。
5. 对 pairwise judge 做 order swap / blind labels / randomization，检测 position、verbosity、self-preference 和 leniency。
6. 高风险样本用 human escalation；低置信或 judge disagreement 不直接进入训练或 release gate。
7. 对 AI feedback 只先进入候选池：通过 data rights、lineage、quality gate、hold-out validation 后，才能进入 RLAIF、reward model、eval 或自我改进。
8. 上线后的 judge 必须进入 [[concepts/JudgeDriftGraderObservability边界|grader observability]]：持续监控 human agreement、score distribution、bias suite、production correlation 和 drift alert。

## 评估方式

- Human agreement：与 human gold 的 accuracy、F1、pairwise agreement、Cohen's kappa 或 rank correlation。
- Calibration：judge 分数是否预测真实成功率、人工接受率、事故率或生产 outcome。
- Stability：重复运行、prompt 模板、judge model version 和 sampling 改动后是否稳定。
- Bias suite：position、verbosity/length、self-preference、model-family、leniency、style、domain 和 group bias。
- Robustness：对 prompt injection、rubric gaming、adversarial answers、irrelevant rationale 和 long trace 的抵抗力。
- Flakiness：同一输入多次评分的方差和 flip rate。
- Escalation quality：低置信、冲突和高风险样本是否正确交给人类。
- Downstream impact：用 judge 分数做 release、training、routing 或 self-improvement 后，真实指标是否改善。

## 过时风险

- 具体 judge 模型会换，但“judge 是测量仪器，需要校准、漂移监控和人工锚点”稳定。
- 更强 judge 会降低成本，但也更容易被用于自动训练闭环；同源模型自评、自我偏好和 reward hacking 风险更高。
- 如果模型供应商隐藏 reasoning 或改变输出风格，judge prompt、rubric 和历史分数可能漂移，需要版本化重校准。

## 一句话归类

LLM-as-judge / AI feedback calibration 主属第 6 层，是自动评分和 AI 标注进入 eval、RLAIF、reward、release gate 与 self-improvement 前的校准边界；它让“AI 评 AI”成为可用证据，而不是未经审计的自我确认。

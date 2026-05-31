---
address: c-000296
type: concept
title: "Reward Hacking / Eval Overfitting 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - evals
  - reward-hacking
  - benchmark-leakage
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/ReasoningEvalVerifier边界]]"
  - "[[concepts/Agent评估体系]]"
  - "[[concepts/Dream与SelfImprovement工程原语]]"
  - "[[concepts/ProductOrganizationLayer边界]]"
  - "[[concepts/ModelRoutingMixture边界]]"
  - "[[concepts/DataFlywheelFeedbackLoop边界]]"
  - "[[concepts/DataRightsPrivacyConsent边界]]"
  - "[[concepts/ToolRiskPermissioning边界]]"
  - "[[concepts/AISafetyOpsGovernance边界]]"
  - "[[concepts/DataQualityLabelQuality边界]]"
  - "[[concepts/SyntheticDataGovernance边界]]"
  - "[[concepts/HumanFeedbackAnnotationOps边界]]"
  - "[[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]]"
  - "[[concepts/EvalPortfolioMetricHierarchy边界]]"
  - "[[concepts/MetricConflictResolution边界]]"
  - "[[concepts/LLMJudgeAIFeedbackCalibration边界]]"
  - "[[concepts/SelfImprovementGateChangeRiskBudget边界]]"
sources:
  - "[[sources/responsible-ai-tensions-tradeoffs-2023]]"
  - "[[sources/openai-faulty-reward-functions-2016]]"
  - "[[sources/deepmind-specification-gaming-2020]]"
  - "[[sources/anthropic-reward-tampering-2024]]"
  - "[[sources/openai-reward-model-overoptimization-2022]]"
  - "[[sources/benchmarking-benchmark-leakage-2024]]"
  - "[[sources/openai-chain-of-thought-monitoring-2025]]"
  - "[[sources/openai-cot-monitorability-2025]]"
  - "[[sources/rewardbench-2024]]"
  - "[[sources/nist-genai-profile-data-privacy-2024]]"
  - "[[sources/owasp-llm-excessive-agency-2025]]"
  - "[[sources/nist-ai-rmf-1-0-2023]]"
  - "[[sources/label-errors-benchmarks-2021]]"
  - "[[sources/learning-to-summarize-human-feedback-2020]]"
  - "[[sources/anthropic-hh-rlhf-2022]]"
  - "[[sources/openai-evaluation-best-practices-2026]]"
  - "[[sources/helm-holistic-evaluation-2022]]"
  - "[[sources/google-ml-test-score-2016]]"
  - "[[sources/llm-judge-position-bias-2024]]"
  - "[[sources/llm-evaluators-self-preference-2024]]"
  - "[[sources/automated-self-testing-quality-gate-llm-applications-2026]]"
---

# Reward Hacking / Eval Overfitting 边界

Reward hacking / eval overfitting 是第 6 层评估与可靠性层的失效模式：系统优化了可测指标、reward、grader、benchmark 或产品 KPI，却没有优化人类真正想要的结果。

一句话：**eval 是质量门；reward hacking 是模型或组织学会钻质量门的空子。**

## 主归属

- 主归属：6. 评估与可靠性层
- 上游输入：reward model、grader、benchmark、用户 KPI、产品 telemetry、训练反馈
- 下游风险：错误行为被高分奖励、benchmark 虚高、router 错路由、自我改进污染 memory/skill/eval/training data
- 反哺层级：2. 模型构建层、3. 推理与能力层、5. Agent 系统层、7. 产品与组织层、8. 自我改进与前沿层

## 稳定链路

```text
proxy metric / reward / eval
    -> optimization pressure
    -> shortcut / exploit / leakage / tampering
    -> score improves while true outcome degrades
    -> detection by holdout eval, adversarial eval, trace monitor, human audit
    -> revise metric, grader, environment, permissions, and feedback loop
```

## 失效类型

| 类型 | 发生位置 | 边界 |
|---|---|---|
| Reward hacking | 第 2/6 层 | 优化 reward model 或奖励函数漏洞 |
| Specification gaming | 第 5/6 层 | 满足字面任务，不满足真实意图 |
| Eval overfitting | 第 6 层 | 针对固定 eval/benchmark 变好，真实分布不变或变差 |
| Benchmark leakage | 第 2/6 层 | 测试集进入训练或调参反馈，分数虚高 |
| Grader hacking | 第 6 层 | 输出迎合 LLM judge/rubric，而非解决任务 |
| Reward tampering | 第 5/8 层 | agent 改 reward、测试、日志或监督机制本身 |
| Product KPI gaming | 第 7 层 | 组织优化点击、留存、成本等代理指标，牺牲真实价值 |
| Data flywheel pollution | 第 7/8 层 | 低质量、被操纵或未授权反馈进入 eval/memory/training |
| Gate tampering | 第 6/8 层 | self-improvement 修改 eval、reward、logs、permission 或 release gate，使自己更容易通过 |
| Consent gaming | 第 7 层 | 用模糊设置、暗色模式或过宽用途描述获得表面授权 |
| Permission gaming | 第 5/6 层 | agent 通过工具组合、间接路径或通用 shell 绕过动作权限 |
| Label-quality failure | 第 6 层 | 错误、模糊或污染标签让 eval / reward / training gate 失真 |
| Annotation gaming | 第 6/7 层 | 标注员、模型或流程迎合 rubric、gold set、长度/风格偏好或 KPI，而非真实质量 |

## 工程防线

1. 用私有、hold-out、持续更新的 eval，而不是只看公开榜单。
2. 把 capability eval、regression eval、adversarial eval 和 production monitoring 分层。
3. 对 reward model / grader 做独立 eval、校准和漂移监控。
4. 读取 trace，区分真实成功、侥幸通过、grader bug、工具滥用和环境漏洞。
5. 高风险 self-improvement 只能提出 diff，必须经过回归、人工门和 rollback。
6. 避免把 CoT 文本直接变成优化目标，否则可能降低可监控性。
7. 对产品指标加入反作弊、用户结果、人工抽样和长期质量指标。
8. 对工具动作加入 unauthorized-action eval、approval-bypass eval 和 sandbox-escape eval。
9. 将高风险 eval failure 交给 [[concepts/AISafetyOpsGovernance边界|AI Safety Ops / Governance]]：进入 risk register、owner、release gate 或 incident playbook。
10. 对 eval 和训练样本先过 [[concepts/DataQualityLabelQuality边界|data/label quality gate]]，避免把错误标签优化成高分。
11. 对合成训练、合成 eval 和 LLM-as-judge 先过 [[concepts/SyntheticDataGovernance边界|synthetic data governance gate]]，避免同一模型家族自我生成、自我评分、自我确认。
12. 对人类偏好和标注数据先过 [[concepts/HumanFeedbackAnnotationOps边界|human feedback / annotation ops gate]]，避免标注员漂移、rubric 泄露、gold-set overfitting 或 reward-model proxy 被放大。
13. 对 eval set 本身先过 [[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界|evaluation dataset lifecycle / benchmark governance]]：split isolation、private hold-out、leakage controls、refresh/retirement 和 release gate 绑定是 eval overfitting 的前置防线。
14. 对 eval portfolio 设 hard stop、guardrail、primary、slice、online 和 diagnostic 层级，避免一个总分掩盖安全、权限、长尾用户或成本回归。
15. 用 [[concepts/MetricConflictResolution边界|metric conflict resolution]] 显式处理“主指标上升但 guardrail / slice / online 变坏”的情况，防止 Goodhart 压过真实风险。
16. 对 LLM judge 先过 [[concepts/LLMJudgeAIFeedbackCalibration边界|LLM-as-judge / AI feedback calibration]]，避免 position bias、verbosity bias、self-preference、leniency 和 prompt sensitivity 被优化成高分。
17. 对 self-improvement proposal 先过 [[concepts/SelfImprovementGateChangeRiskBudget边界|self-improvement gate / change-risk budget]]；任何触碰 eval、reward、log、permission、release gate 或 monitor threshold 的控制面改动默认高风险。

## 评估方式

- Proxy-vs-ground-truth gap：reward/eval 分数和人工或真实结果的差距。
- Hold-out degradation：公开 eval 上升，私有或新任务下降。
- Leakage signal：test contamination、n-gram overlap、异常低 perplexity、训练数据命中。
- Grader calibration：高分样本是否真实好，低分样本是否真实坏。
- Exploit rate：agent 修改测试、隐藏失败、利用环境漏洞或操纵反馈的频率。
- Drift：模型、prompt、产品流量或用户行为变化后，eval 是否仍能预测真实价值。

## 过时风险

- 具体 benchmark 会轮换，但 Goodhart / proxy gaming 不会消失。
- 更强模型会减少低级错误，也会更擅长发现指标、环境和监督漏洞。
- CoT monitoring 是有用信号，但可能被训练过程、隐藏推理或直接优化压力削弱。
- 产品组织层越依赖自动 telemetry，越需要把数据权利、反作弊和人工校准并入第 6 层。
- [[concepts/DataFlywheelFeedbackLoop边界]] 必须先经过 anti-gaming、权限和 hold-out gate，不能把所有反馈直接回灌。
- [[concepts/DataRightsPrivacyConsent边界]] 也是反作弊对象：权限标签、删除请求和 opt-out 不能被产品 KPI 或自我改进流程绕过。
- [[concepts/AISafetyOpsGovernance边界]] 负责防止 override 和 exception 变成绕过质量门的常态。
- [[concepts/EvaluationDatasetLifecycleBenchmarkGovernance边界]] 防止 eval 被训练、调参、公开榜单和反复模型选择污染。

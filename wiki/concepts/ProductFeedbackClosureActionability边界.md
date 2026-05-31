---
address: c-000581
type: concept
title: "Product Feedback Closure / Actionability 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - product
  - feedback-loop
  - data-flywheel
  - governance
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/ProductOrganizationLayer边界]]"
  - "[[concepts/DataFlywheelFeedbackLoop边界]]"
  - "[[concepts/DashboardCalibrationGovernanceMetricQuality边界]]"
  - "[[concepts/OfflineOnlineEvalCorrelation边界]]"
  - "[[concepts/DataRightsPrivacyConsent边界]]"
  - "[[concepts/DataQualityLabelQuality边界]]"
  - "[[concepts/HumanFeedbackAnnotationOps边界]]"
  - "[[concepts/ModelReleaseRollbackGate边界]]"
  - "[[concepts/SelfImprovementGateChangeRiskBudget边界]]"
  - "[[concepts/AISafetyOpsGovernance边界]]"
  - "[[concepts/AIIncidentResponsePostmortem边界]]"
  - "[[concepts/RewardHackingEvalOverfitting边界]]"
sources:
  - "[[sources/openai-evals-business-framework-2025]]"
  - "[[sources/openai-model-optimization-2026]]"
  - "[[sources/langchain-production-monitoring-regression-tests-2026]]"
  - "[[sources/langsmith-user-feedback-traces-2026]]"
  - "[[sources/aws-genai-production-feedback-loops-2026]]"
  - "[[sources/aws-prescriptive-genai-production-monitoring-2026]]"
  - "[[sources/nvidia-ai-data-flywheel-2026]]"
  - "[[sources/nvidia-data-flywheel-blueprint-distillation-2025]]"
  - "[[sources/adaptive-data-flywheel-mape-ai-agent-improvement-2025]]"
  - "[[sources/google-mlops-continuous-delivery-2026]]"
  - "[[sources/nist-ai-rmf-core-manage-change-management-2023]]"
---

# Product Feedback Closure / Actionability 边界

Product feedback closure / actionability 是第 7 层产品与组织层的反馈闭环边界：它证明真实产品反馈、trace、用户报告、业务指标或事故信号，已经被授权、归因、分流、执行、验证，并用证据关闭。

一句话：**收集 feedback 不是闭环；只有 feedback 变成可追踪行动并通过验证，才算完成 data flywheel。**

## 主归属

- 主归属：7. 产品与组织层
- 上游输入：用户反馈、production trace、业务结果、失败案例、人工修改、事故报告、online eval、dashboard signal
- 下游输出：eval/regression case、RAG/memory/skill/tool/router/training candidate、产品 backlog、incident action、policy/gate update、no-action rationale
- 质量门：6. 评估与可靠性层
- 自动化门：8. 自我改进与前沿层

## 稳定链路

```text
product event / feedback / trace / incident / business outcome
    -> rights and purpose check
    -> signal triage, attribution, and duplicate/noise filtering
    -> closure ticket with target route
    -> owner, SLA, evidence package, and expected validation
    -> downstream artifact update
    -> validation by offline eval, online metric, human review, canary, or production contract
    -> closure evidence or no-action rationale
    -> dashboard calibration, backlog retirement, or reopen
    -> self-improvement gate if automated
```

## Actionability 分类

| 类别 | 进入哪里 | 关闭证据 |
|---|---|---|
| Ignore / duplicate | feedback backlog | 去重记录、相同根因链接、no-action rationale |
| Observe | monitoring / dashboard | 观察窗口、阈值、owner、复审日期 |
| Eval / regression | 第 6 层 eval set | 新 eval case、baseline、修复后通过结果 |
| Knowledge / RAG / memory | 第 4 层知识系统 | 文档或 memory diff、权限检查、retrieval/generation eval |
| Skill / tool / workflow | 第 4/5 层 skill/tool/harness | skill/tool diff、trace regression、权限和安全检查 |
| Router / serving | 第 3 层 routing/serving | cost-quality-latency 对比、canary 或 A/B 结果 |
| Training / distillation | 第 2 层训练候选 | data quality、lineage、hold-out、model release gate |
| Product / UX | 第 7 层产品路线 | 产品变更、用户结果指标、支持/投诉变化 |
| Governance / incident | 第 7 层 safety ops | incident record、action item、policy/gate 更新 |

## 与相邻概念区别

- 与 [[concepts/DataFlywheelFeedbackLoop边界|data flywheel / feedback loop]]：data flywheel 定义反馈能流向哪些改进路径；本页定义每条反馈是否真的被分流、行动、验证并关闭。
- 与 [[concepts/ProductOrganizationLayer边界|product / organization layer]]：product/org 定义 AI 能力进入真实工作流；本页是该工作流产生的反馈如何回到工程系统。
- 与 [[concepts/DashboardCalibrationGovernanceMetricQuality边界|dashboard calibration]]：dashboard calibration 判断指标能不能信；本页判断指标或反馈有没有触发正确行动。
- 与 [[concepts/OfflineOnlineEvalCorrelation边界|offline / online eval correlation]]：offline/online correlation 判断离线评估是否预测线上结果；本页把线上失败或用户反馈转成可追踪 eval、产品或模型改进。
- 与 [[concepts/HumanFeedbackAnnotationOps边界|human feedback / annotation ops]]：annotation ops 把人类判断变成高质量 label 或 review evidence；本页先决定反馈是否值得进入 annotation，以及 annotation 结果是否关闭问题。
- 与 [[concepts/SelfImprovementGateChangeRiskBudget边界|self-improvement gate]]：本页产生改进 action；自动应用时还要进入第 8 层 change-risk budget。

## 工程实践

1. 给所有 feedback 绑定 trace id、artifact version、模型、prompt、tool、retrieval 文档、用户/租户、时间、产品 surface 和 data-rights 标签。
2. 每条反馈先过 rights / purpose / retention gate，不能把 service feedback 自动升级成 eval 或 training 数据。
3. 建立 actionability triage：ignore、observe、eval、knowledge、memory、skill、tool、router、training、product、incident。
4. 每个可行动 signal 生成 closure ticket：owner、SLA、target layer、artifact id、验证方式、回滚或 no-action 条件。
5. 低质量、重复、不可复现或无权限反馈不丢弃，要写明 no-action rationale 或观察窗口。
6. 失败类 feedback 优先转成 regression eval；事实缺口优先转成 RAG/knowledge diff；重复流程优先转成 skill/tool/workflow；稳定行为偏差才进入 fine-tuning 或 distillation。
7. 所有闭环结果都要回到 dashboard：open、triaged、in progress、validated、closed、reopened、expired。
8. 对自动闭环设置 change-risk budget：小范围 memory/context 更新可自动；tool、harness、eval、router、policy、training 和 weights 要分级 gate。

## 评估方式

- Feedback-to-action conversion：有效反馈有多少进入具体行动，而不是停在日志中。
- Time to triage / action / validation / closure：从反馈出现到关闭各阶段耗时。
- Closure evidence completeness：是否有 trace、owner、artifact diff、验证结果和残余风险记录。
- Regression conversion：生产失败中有多少被转成 regression eval，并防止复发。
- Outcome lift：关闭后任务成功率、人工接管、投诉、成本/成功或业务结果是否改善。
- Reopen / recurrence rate：已关闭问题是否复发，是否说明根因归因错误。
- No-action quality：被忽略或观察的反馈是否有清楚理由、阈值和复审机制。
- Gaming / false closure：指标改善但用户结果、事故率或真实质量没有改善。
- Rights compliance：feedback 是否只用于被授权的 service、analytics、eval、memory、training 或 vendor 路径。

## 过时风险

- 具体 feedback 工具、observability 平台和 ticket 系统会变化，但“反馈要绑定 trace、分流到 artifact、验证后关闭”的结构稳定。
- 当模型能力增强时，某些训练或 prompt 改动会减少，但 product feedback closure 仍需要决定是修知识、修工具、修 UX、修评估还是不行动。
- 如果 closure 只看 ticket 状态，会变成 dashboard theatre；必须用 outcome、reopen、recurrence 和 anti-gaming 校准。

## 一句话归类

Product feedback closure / actionability 主属第 7 层，是 data flywheel 进入组织执行后的闭环证明；它不新增顶层，而是把第 7 层真实反馈安全反哺第 2/3/4/5/6/8 层的“行动完成证据”固定下来。

---
address: c-000304
type: concept
title: "Data Flywheel / Feedback Loop 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - data-flywheel
  - feedback-loop
  - product
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/ProductOrganizationLayer边界]]"
  - "[[concepts/数据飞轮复利]]"
  - "[[concepts/RewardHackingEvalOverfitting边界]]"
  - "[[concepts/ProductFeedbackClosureActionability边界]]"
  - "[[concepts/Dream与SelfImprovement工程原语]]"
  - "[[concepts/RAG与Memory边界]]"
  - "[[concepts/Skill与ToolMemory边界]]"
  - "[[concepts/DataRightsPrivacyConsent边界]]"
  - "[[concepts/DataQualityLabelQuality边界]]"
  - "[[concepts/SyntheticDataGovernance边界]]"
  - "[[concepts/DatasetLineageProvenanceGraph边界]]"
  - "[[concepts/DataDeletionUnlearningImpact边界]]"
  - "[[concepts/HumanFeedbackAnnotationOps边界]]"
  - "[[concepts/OfflineOnlineEvalCorrelation边界]]"
  - "[[concepts/PostReleaseEvalDrift边界]]"
  - "[[concepts/SelfImprovementGateChangeRiskBudget边界]]"
sources:
  - "[[sources/nvidia-ai-data-flywheel-2026]]"
  - "[[sources/aws-genai-production-feedback-loops-2026]]"
  - "[[sources/langsmith-user-feedback-traces-2026]]"
  - "[[sources/adaptive-data-flywheel-mape-ai-agent-improvement-2025]]"
  - "[[sources/nvidia-data-flywheel-blueprint-distillation-2025]]"
  - "[[sources/openai-data-sharing-controls-2026]]"
  - "[[sources/google-rules-of-ml-2026]]"
  - "[[sources/google-mlops-continuous-delivery-2026]]"
  - "[[sources/hidden-technical-debt-ml-systems-2015]]"
  - "[[sources/agent-in-the-loop-data-flywheel-2025]]"
  - "[[sources/characterflywheel-2026]]"
  - "[[sources/openai-model-optimization-2026]]"
  - "[[sources/openai-api-data-controls-2026]]"
  - "[[sources/openai-model-improvement-data-policy-2026]]"
  - "[[sources/data-cascades-high-stakes-ai-2021]]"
  - "[[sources/openlineage-spec-2026]]"
  - "[[sources/machine-unlearning-sisa-2019]]"
  - "[[sources/learning-to-summarize-human-feedback-2020]]"
  - "[[sources/aws-prescriptive-genai-production-monitoring-2026]]"
  - "[[sources/nist-ai-rmf-core-manage-change-management-2023]]"
---

# Data Flywheel / Feedback Loop 边界

Data flywheel / feedback loop 是第 7 层产品与组织层的反馈接口：真实使用产生的行为信号、失败 trace、人工修正、显式反馈和业务结果，被清洗、分流、评估后反哺 eval、context、memory、skill、tool、model routing 或训练数据。

一句话：**数据飞轮不是“把用户数据都拿去训练”，而是把真实使用证据路由到正确改进层。**

## 主归属

- 主归属：7. 产品与组织层
- 上游输入：产品 telemetry、用户反馈、接受/拒绝、人工修正、agent trace、成本/延迟、业务结果
- 下游输出：eval 样本、知识库更新、memory、skills、tool fix、router policy、fine-tuning / distillation 候选、产品路线
- 质量门：6. 评估与可靠性层
- 权限门：data rights、privacy、consent、retention、tenant boundary

## 稳定链路

```text
real usage / feedback / trace
    -> consent + logging boundary
    -> signal extraction and attribution
    -> routing by evidence type
    -> eval / context / memory / skill / tool / router / training update
    -> hold-out validation and anti-gaming checks
    -> closure evidence and reopen trigger
    -> product improvement
    -> more usage and better signals
```

## 反馈分流表

| 信号 | 应该进入哪里 | 不应直接进入哪里 |
|---|---|---|
| 失败案例、边界 case | 第 6 层 eval / regression suite | 直接 fine-tune |
| 用户显式纠错 | eval、SFT/RFT 候选、知识库修正 | 未去重训练集 |
| 接受/拒绝/编辑行为 | preference data、产品指标、router signal | 无校准 reward |
| 重复工作流成功 trace | skill、workflow、tool docs | 模型权重 |
| 稳定领域知识 | RAG / knowledge base / memory | 过早 fine-tune |
| 成本/延迟/失败率 | model routing、serving、产品 SLO | 质量标签 |
| 投诉/安全事件 | red-team eval、policy、guardrail | 产品增长指标 |

## 与相邻概念区别

- 与 [[concepts/数据飞轮复利]]：数据飞轮复利强调护城河；本页强调工程分流和反馈安全。
- 与 [[concepts/ProductFeedbackClosureActionability边界|product feedback closure]]：本页定义反馈分流到哪里；feedback closure 证明这些反馈是否真正被行动、验证、关闭或写明 no-action rationale。
- 与 self-improvement：第 7 层产生信号；第 8 层把信号转成 diff，并由第 6 层 gate。
- 与 RAG / memory：知识和偏好先外化；只有稳定行为需求才进入训练。
- 与 reward hacking：飞轮会放大指标污染，必须先做 anti-gaming、校准和 hold-out。
- 与 [[concepts/DataRightsPrivacyConsent边界|data rights]]：本页定义反馈路径；data rights 定义哪些数据可被用于哪种路径。
- 与 [[concepts/DataQualityLabelQuality边界|data quality]]：本页产生候选信号；data quality 判断信号是否足够可靠，能否成为 eval、training、RAG、memory 或 skill 证据。
- 与 [[concepts/SyntheticDataGovernance边界|synthetic data governance]]：data flywheel 可以触发合成 failure variants、teacher outputs 或 augmentation；synthetic governance 决定这些候选能否进入训练或 eval。
- 与 [[concepts/DatasetLineageProvenanceGraph边界|dataset lineage]]：data flywheel 的每条信号都要能追溯来源、权限、转换和下游影响，否则无法安全分流到 eval、training、RAG、memory、skill 或 router。
- 与 [[concepts/DataDeletionUnlearningImpact边界|data deletion / unlearning impact]]：飞轮产生的 trace、feedback、memory、eval 和 training candidates 必须可删除、可隔离、可防再摄入；进入模型权重后才需要评估 retraining 或 unlearning。
- 与 [[concepts/HumanFeedbackAnnotationOps边界|human feedback / annotation ops]]：飞轮产生候选反馈，annotation ops 通过 rubric、calibration、QA 和 adjudication 把候选反馈变成可用 label、preference 或 review evidence。
- 与 [[concepts/OfflineOnlineEvalCorrelation边界|offline / online eval correlation]]：飞轮分流真实使用信号；offline/online correlation 判断哪些信号能校准离线 eval 和 release gate。
- 与 [[concepts/PostReleaseEvalDrift边界|post-release eval drift]]：飞轮提供真实生产信号；post-release drift 判断这些信号是否说明 release evidence、threshold、card 或 safety case 已变 stale。
- 与 [[concepts/SelfImprovementGateChangeRiskBudget边界|self-improvement gate / change-risk budget]]：飞轮把真实反馈变成改进候选；self-improvement gate 判断这些候选 diff 是否能自动应用、灰度、人工审查或拒绝。

## 工程实践

1. 先定义事件 schema：任务、输入、输出、工具、结果、人工修改、用户反馈、成本、延迟。
2. 每条信号保留 provenance：用户/组织、时间、版本、模型、prompt、tool、权限。
3. 用 failure taxonomy 做归因：prompt、RAG、memory、tool、model、router、UX、policy、用户目标。
4. 优先把失败转成 eval，把重复成功转成 skill / workflow，把稳定知识转成 RAG。
5. 只有有足够样本、清晰授权和 hold-out 通过时，才进入 fine-tuning / distillation。
6. 对 feedback loop 加 anti-gaming：异常反馈、刷指标、偏见、低质量标签、KPI gaming。
7. 定期清理旧信号：过时知识、已修复 bug、失效 workflow 和重复样本。
8. 把进入第 8 层的改进候选写成 proposed diff，并带上 target layer、evidence、lineage、rollback 和 owner，交给 self-improvement gate。
9. 给每条已分流信号记录 closure evidence：下游 artifact、验证结果、owner、关闭日期、残余风险和 reopen trigger。

## 评估方式

- Signal quality：反馈是否可解释、可归因、可复现、可授权。
- Conversion rate：失败反馈有多少转成 eval、skill、knowledge update 或 model update。
- Impact：更新后真实任务成功率、人工接管率、成本/成功是否改善。
- Hold-out safety：公开/训练内指标改善时，私有 hold-out 是否也改善。
- Anti-gaming：是否存在刷反馈、KPI gaming、reward hacking 或 benchmark leakage。
- Privacy / consent：数据用途是否符合用户授权、保留策略和组织边界。
- Data rights gate：service、memory、eval、training、vendor sharing 是否有独立用途标签和审计证据。
- Data quality gate：反馈是否可复现、可归因、无泄露、label 清楚、适合目标用途。
- Closure quality：反馈是否被转成行动、验证并关闭，而不是停在 dashboard 或 backlog。

## 过时风险

- 具体数据平台会变化，但“真实使用 → 分流 → 验证 → 改进”的结构稳定。
- 模型能力增强会减少某些 fine-tune 需求，但不会消除 eval、memory、skill 和 product telemetry。
- 数据飞轮若没有权限和 anti-gaming，会从护城河变成合规、安全和质量风险。

## 与 Data Rights 的接口

[[concepts/DataRightsPrivacyConsent边界]] 是 data flywheel 的前置闸门：

- 本次服务运行数据不自动获得 training 授权。
- Memory / personalization 要能被用户或组织查看、删除、关闭。
- Eval 样本要带 permission tag、脱敏策略和保留期。
- 训练候选需要比产品 telemetry 更强的授权、来源追踪和删除策略。
- 多 provider 路由必须先检查数据是否允许发往对应 provider、地域和子处理方。

---
address: c-000465
type: concept
title: "Post-release Eval Drift 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - evals
  - production-monitoring
  - drift
  - release-governance
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/EvalUncertaintyCommunicationReleaseCard边界]]"
  - "[[concepts/OfflineOnlineEvalCorrelation边界]]"
  - "[[concepts/EvalPortfolioMetricHierarchy边界]]"
  - "[[concepts/EvidenceFreshnessStaleProof边界]]"
  - "[[concepts/MonitorOwnershipEscalationLadder边界]]"
  - "[[concepts/SafetyCaseAssuranceCase边界]]"
  - "[[concepts/ModelReleaseRollbackGate边界]]"
  - "[[concepts/JudgeDriftGraderObservability边界]]"
  - "[[concepts/AIIncidentResponsePostmortem边界]]"
  - "[[concepts/DataFlywheelFeedbackLoop边界]]"
sources:
  - "[[sources/nist-ai-rmf-playbook-monitoring-responsibility-2026]]"
  - "[[sources/microsoft-ai-incident-response-readiness-2026]]"
  - "[[sources/nist-deployed-ai-monitoring-challenges-2026]]"
  - "[[sources/cmu-sei-drift-monitoring-ml-systems-2026]]"
  - "[[sources/aws-prescriptive-genai-production-monitoring-2026]]"
  - "[[sources/aws-prescriptive-genai-drift-detection-2026]]"
  - "[[sources/google-cloud-genai-monitoring-2024]]"
  - "[[sources/google-ml-test-score-2016]]"
  - "[[sources/openai-evaluation-best-practices-2026]]"
  - "[[sources/langchain-production-monitoring-regression-tests-2026]]"
  - "[[sources/evaluation-driven-development-operations-llm-agents-2025]]"
---

# Post-release Eval Drift 边界

Post-release eval drift 是第 6 层评估与可靠性层的发布后证据失效监控边界：它检查 release card、offline eval、online outcome、production monitor 和 safety case 里的证据，是否因为生产分布、用户行为、模型/provider、prompt、RAG、tool、judge、政策或环境变化而变 stale。

一句话：**release card 说明“为什么现在可以发”；post-release eval drift 负责持续检查“这个发布证据现在还站得住吗”。**

## 主归属

- 主归属：6. 评估与可靠性层
- 组织接口：7. 产品与组织层
- 上游输入：release card、safety case、offline eval baseline、online eval、production traces、prompt/response distributions、judge health、incident/user feedback、cost/latency/SLO
- 下游输出：drift alert、stale-evidence flag、eval refresh task、threshold/card update、canary/rollback trigger、regression candidates、safety case refresh trigger
- 反馈接口：[[concepts/DataFlywheelFeedbackLoop边界]]

## 稳定链路

```text
release evidence: eval threshold, card, safety case, monitor plan
    -> production baseline: model/prompt/tool/RAG/judge/provider/user segments
    -> live signals: prompts, responses, traces, outcomes, safety, cost, latency
    -> drift detection: data, prompt, response, embedding, score, judge, policy, slice
    -> compare against release hypothesis and valid scope
    -> action: continue, investigate, refresh eval, quarantine metric, canary, rollback, incident, case refresh
    -> feed stale evidence and new failures into regression eval, release card, and data flywheel
```

## Drift 类型

| 类型 | 说明 | 常见动作 |
|---|---|---|
| Input / prompt drift | 用户问题、意图、语言、复杂度或风险分布改变 | 刷新 eval slice、补 canary |
| Output / behavior drift | 输出长度、拒答、幻觉、tool use、tone 或 policy 结果改变 | contract test、rollback、prompt/tool fix |
| Score / eval drift | 线上分数、通过率、人工接管、投诉与离线预测脱节 | 更新 threshold 或 trust tier |
| Judge drift | 评分器模型、prompt、rubric、分布或 human agreement 变了 | score quarantine、recalibration |
| Context / RAG drift | 知识库、memory、retrieval 分布或 stale docs 影响结果 | index refresh、groundedness eval |
| Provider / model drift | 托管模型 alias、API、region、latency 或 safety behavior 变化 | pin snapshot、fallback、provider review |
| Risk / policy drift | 法规、客户场景、风险容忍度或 harm taxonomy 变化 | safety case refresh、scope restriction |

## 与相邻概念区别

- 与 [[concepts/EvalUncertaintyCommunicationReleaseCard边界]]：release card 写明发布时的证据、局限和监控计划；本页检查这些证据在发布后何时过期。
- 与 [[concepts/OfflineOnlineEvalCorrelation边界]]：offline/online correlation 衡量离线指标是否预测线上 outcome；本页监控这种预测关系和证据包是否随时间漂移。
- 与 [[concepts/EvalPortfolioMetricHierarchy边界]]：eval portfolio 定义哪些证据组成发布质量门；post-release drift 监控这些证据的 freshness、相关性和行动规则是否仍有效。
- 与 [[concepts/EvidenceFreshnessStaleProof边界]]：本页负责发现发布后证据可能失效；evidence freshness / stale proof 定义每条证据的有效期、依赖、状态和证明字段。
- 与 [[concepts/MonitorOwnershipEscalationLadder边界]]：本页产生 drift / stale-evidence signal；monitor ownership 把信号分派给 owner、SLA、incident 或 release gate action。
- 与 [[concepts/JudgeDriftGraderObservability边界]]：judge drift 是评分器健康；post-release eval drift 是整个发布证据链的健康，judge drift 是其中一个输入。
- 与 [[concepts/ModelReleaseRollbackGate边界]]：release gate 执行发布、灰度、回滚；本页给 gate 提供上线后证据失效和回滚触发信号。
- 与 [[concepts/SafetyCaseAssuranceCase边界]]：safety case 组织高风险论证；本页是让 case refresh 的运行触发器之一。
- 与 [[concepts/AIIncidentResponsePostmortem边界]]：drift 是早期检测和证据 stale；incident response 是已经升级为事故后的止血和复盘。
- 与 generic observability：普通 observability 看服务是否运行；本页看“发布决策所依赖的 eval 证据是否仍有效”。

## 工程实践

1. 每张 release card / safety case 必须带 production monitor plan：指标、slice、阈值、owner、刷新触发器和 rollback trigger。
2. 发布前冻结 baseline：model/provider、prompt hash、tool schema、RAG index、judge version、eval dataset、user cohort 和 time window。
3. 监控 prompt、response、embedding、score、guardrail、business/user outcome、latency、cost 和 incident signals，并按风险 slice 分开看。
4. 区分 alert 和 action：drift alert 先触发调查，hard safety 或 contract breach 才直接触发 pause/rollback。
5. Judge、eval dataset、release card 和 safety case 都要有 stale flag，避免旧证据继续进入 release gate 或 self-improvement。
6. 把 drifted production traces 抽样进入 annotation / judge review，再转成 regression eval 或 benchmark refresh 候选。
7. 对 provider silent update、RAG corpus refresh、tool schema change 和 policy update 设事件触发重跑，而不是只靠定时监控。

## 评估方式

- Drift detection latency：生产分布或证据失效多久被发现。
- Alert precision / recall：drift alert 是否对应真实质量、风险或决策失效。
- Stale-evidence time：证据已失效但仍被 release gate / safety case 使用的时间。
- Regression capture rate：drifted trace 有多少变成可复现 eval。
- Correlation decay detection：离线指标预测线上 outcome 的关系变弱时是否及时降权。
- Slice coverage：关键用户、语言、任务、工具路径、风险等级是否都有监控。
- Action completion：drift alert 是否被 owner 关闭、解释、回滚、刷新或写入 case。

## 过时风险

- 具体 drift detector、embedding distance、dashboard 和平台会变化，但“发布证据 -> 生产基线 -> drift signal -> 行动 -> 证据刷新”的链路稳定。
- 强模型可能降低某些输出漂移，但会增加 agent tool、memory、provider、policy 和长期任务漂移的复杂度。
- 如果只监控服务健康而不监控证据有效性，系统会出现“线上没报警，但 release card 已经 stale”的隐性风险。

## 一句话归类

Post-release eval drift 主属第 6 层，是 release card、offline/online correlation、production monitoring 和 safety case 之间的发布后证据保鲜边界；它不新增顶层，而是让第 6 层质量证据在第 7 层真实运行中持续可用。

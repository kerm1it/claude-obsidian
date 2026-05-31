---
address: c-000504
type: concept
title: "Monitor Tabletop / Runbook Drill 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - monitoring
  - tabletop
  - runbook
  - incident-response
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/MonitorOwnershipEscalationLadder边界]]"
  - "[[concepts/AIIncidentResponsePostmortem边界]]"
  - "[[concepts/ModelReleaseRollbackGate边界]]"
  - "[[concepts/AISafetyOpsGovernance边界]]"
  - "[[concepts/EvalUncertaintyCommunicationReleaseCard边界]]"
  - "[[concepts/EvidenceFreshnessStaleProof边界]]"
  - "[[concepts/MetricConflictResolution边界]]"
  - "[[concepts/MultiProviderGovernance边界]]"
sources:
  - "[[sources/google-sre-incident-management-guide-2026]]"
  - "[[sources/google-sre-managing-incidents-2016]]"
  - "[[sources/microsoft-ai-incident-response-readiness-2026]]"
  - "[[sources/nist-sp800-84-tte-program-2006]]"
  - "[[sources/ncsc-effective-steps-cyber-exercise-creation-2026]]"
  - "[[sources/aws-security-ir-simulations-2026]]"
  - "[[sources/cisa-ai-cyber-tabletop-exercise-series-2025]]"
  - "[[sources/fema-hseep-exercise-evaluation-2020]]"
---

# Monitor Tabletop / Runbook Drill 边界

Monitor tabletop / runbook drill 是第 7 层产品与组织层的演练验证边界：它把第 6 层 monitor、eval breach、stale evidence、release-card watch item、provider alert 和 user report，变成可演练场景，用来验证 owner、on-call、incident command、release gate、risk owner、comms、legal/support 和 provider POC 是否真的能在压力下接上。

一句话：**monitor ownership 写责任链；tabletop / drill 验证责任链会不会动。**

## 主归属

- 主归属：7. 产品与组织层
- 质量输入：6. 评估与可靠性层
- 上游输入：monitor signal、runbook、release card、safety case、incident playbook、provider policy、risk threshold、contract test result
- 下游输出：exercise finding、gap list、after-action report、improvement plan、updated runbook、new monitor/eval/release gate action
- 反哺层级：6. eval/monitoring、7. incident/release/governance、8. self-improvement backlog

## 稳定链路

```text
scenario seed: eval breach / stale evidence / provider drift / user harm / tool misuse
    -> exercise objective, scope, participants, risk tier, success criteria
    -> inject timeline: alerts, ambiguous signals, conflicting metrics, stakeholder pressure, provider response
    -> run tabletop or controlled drill with monitor owner, on-call, IC, Ops, Comms, risk owner
    -> observe decisions: ack, triage, escalate, elevate, hold rollout, rollback, notify, preserve evidence
    -> after-action report: what worked, what failed, missing authority, missing data, slow handoff
    -> improvement plan: owner, due date, runbook diff, monitor/eval/gate update, re-drill trigger
```

## AI 演练场景

| 场景 | 要验证什么 |
|---|---|
| Judge drift 让 release card 证据变 stale | freshness、grader owner、release owner 和 risk owner 是否会降权旧证据 |
| Provider silent update 触发 contract regression | provider POC、compatibility suite、release gate、fallback path 是否有效 |
| Prompt injection 诱导高风险工具动作 | on-call、tool disable、credential revoke、用户沟通和 evidence package |
| RAG / memory 泄露或错误引用敏感数据 | data rights、lineage、incident response、deletion/unlearning handoff |
| Safety guardrail 破线但 primary metric 上升 | metric conflict、hard stop、override denial、risk elevation |
| 签名 eval artifact 验证失败 | evidence quarantine、rerun eval、block release、attestation owner |
| 多团队 monitor 同时触发 | IC、Ops、Comms、Planning、external provider handoff |

## 与相邻概念区别

- 与 [[concepts/MonitorOwnershipEscalationLadder边界]]：ownership ladder 定义谁响应、何时升级、能做什么；tabletop/drill 用模拟场景验证这些定义是否可执行。
- 与 [[concepts/AIIncidentResponsePostmortem边界]]：incident response 处理真实事故；tabletop/drill 在受控环境中提前暴露角色、权限、证据和沟通缺口。
- 与 runbook：runbook 是说明书；drill 检查说明书是否能被值班人员按时执行。
- 与 [[concepts/ModelReleaseRollbackGate边界]]：release gate 执行 hold/canary/rollback；演练验证 gate owner、审批权限、rollback trigger 和 fallback 路径是否清楚。
- 与 [[concepts/AISafetyOpsGovernance边界]]：safety ops 是完整风险运行系统；演练是验证风险运行系统是否会在压力下失效的机制。
- 与 red team：red team 找技术或策略弱点；tabletop/drill 验证组织响应、交接、证据保全和决策权限。

## 工程实践

1. 每次演练只围绕一个高价值场景，不把所有事故类型塞进一个会。
2. 写清 exercise objective、participants、scope、rules of engagement、real-world stop condition 和 success criteria。
3. 使用 injects 推进：alert、用户报告、provider status、conflicting metric、legal/comms pressure、missing evidence、rollback failure。
4. 标记所有沟通为 exercise，避免误触发真实客户、监管或供应商流程；live drill 需要 change freeze 和安全保护。
5. 观察员记录时间线、角色交接、证据缺口、权限阻塞、runbook 偏差、决策理由和沟通质量。
6. After-action report 不能只写总结，必须有 owner、due date、验收证据、re-drill trigger 和 release-gate / monitor / eval 更新。
7. 高风险 AI 系统至少演练：provider drift、tool misuse、stale evidence、metric conflict、privacy/data incident、rollback/fallback。

## 评估方式

- Exercise coverage：关键 monitor、风险阈值、release gate、provider path 和 data incident 是否被周期性演练。
- Role readiness：monitor owner、on-call、IC、Ops、Comms、risk owner 是否知道自己的入口和权限。
- Ack / triage / escalation time：演练中从 signal 到确认、分级、升级和行动的时间。
- Runbook completion：关键步骤是否能按顺序执行，是否需要临时知识或隐性权限。
- Handoff quality：交接是否有 state doc、owner、next action、due time 和 closure evidence。
- Decision quality：是否正确处理 hard stop、metric conflict、stale evidence、provider ambiguity 和 rollback。
- Improvement closure：AAR/IP action item 是否按期关闭，并在下一次 drill 中验证。

## 过时风险

- 演练场景会随模型能力、provider 功能、工具权限和产品流程变化而 stale；场景库必须从真实 incident、near miss、release card watch item 和 post-release drift 中刷新。
- Tabletop 不能证明系统安全，只能证明人员、流程和权限在模拟条件下可用；必须连接真实 eval、monitor、release gate 和 incident metrics。
- 如果没有 after-action owner、due date 和 re-drill，演练会退化成合规仪式。

## 一句话归类

Monitor tabletop / runbook drill 主属第 7 层，是把第 6 层监控和评估信号转成组织演练、after-action report 和改进闭环的验证边界；它不新增顶层，而是检验 monitor ownership、incident response、release gate 和 safety ops 是否真的可执行。

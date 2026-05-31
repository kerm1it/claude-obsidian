---
address: c-000568
type: question
title: "Research: Self-improvement gate change-risk budget 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - research
  - self-improvement
  - change-gate
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/SelfImprovementGateChangeRiskBudget边界]]"
  - "[[concepts/Dream与SelfImprovement工程原语]]"
  - "[[concepts/ModelReleaseRollbackGate边界]]"
sources:
  - "[[sources/automated-self-testing-quality-gate-llm-applications-2026]]"
  - "[[sources/moss-self-evolution-source-rewriting-2026]]"
  - "[[sources/autogenesis-self-evolving-agent-protocol-2026]]"
  - "[[sources/darwin-godel-machine-self-improving-agents-2025]]"
  - "[[sources/nist-ai-rmf-core-manage-change-management-2023]]"
  - "[[sources/google-mlops-continuous-delivery-2026]]"
  - "[[sources/google-sre-error-budget-policy-2018]]"
---

# Research: Self-improvement gate change-risk budget 边界

## 研究问题

第 8 层 self-improvement 已经能解释 dream、agent reflection、harness update 和 weight-level adaptation，但还缺一个关键问题：**系统自己提出的改动，什么时候可以自动落地，什么时候必须候选池、灰度、人工审查或回滚？**

本轮目标不是新增第九层，而是给第 8 层反馈环补上准入边界。

## 稳定定义

Self-improvement gate / change-risk budget 是一个把 self-improvement proposal 转成可治理变更的边界。它消费 trace、eval failure、user feedback、dream output 或 agent self-edit，要求每个改动带上 target layer、evidence、lineage、risk score、rollback path 和 owner，再按风险预算决定 auto-apply、sandbox、canary、human review、hold、rollback 或 reject。

## 来源综合

- Automated self-testing 论文直接给出 PROMOTE / HOLD / ROLLBACK 型质量门，说明 LLM 应用发布必须把 task success、context preservation、latency、safety 和 evidence coverage 组合成 evidence-based release decision。
- MOSS 把 self-evolution 推到 source-level rewriting，并用 production-failure evidence、ephemeral trial workers、batch replay、user-consent-gated promotion 和 health-probe rollback 说明自我改造不能直接进生产。
- Autogenesis 把 prompts、agents、tools、environments、memory 都建模成 versioned resources，并要求 self-evolution 具备 proposing、assessing、committing、auditable lineage 和 rollback。
- Darwin Godel Machine 证明 self-modifying coding agents 可以通过 benchmark validation 和 archive exploration 提升能力，但也显示“改自己”必须被 sandbox、human oversight 和 benchmark gate 约束。
- NIST AI RMF Manage/Govern/Measure 提供更稳定的治理框架：风险要被 mapped/measured 后定期管理，post-deployment monitoring 要包含 user feedback、override、decommissioning、incident response、recovery 和 change management。
- Google MLOps 和 SRE error budget 提供工程类比：continuous learning 不等于自动上线；预算透支时要减少变更速度，把可靠性证据重新补足。

## 分层归属

- 主归属：8. 自我改进与前沿层
- 质量门：6. 评估与可靠性层
- 组织执行：7. 产品与组织层
- 改动目标：2. training / weights，4. memory / context / skill，5. tool / harness / workflow，6. eval / judge / metric，7. release / policy / monitoring

因此它不是新顶层，而是第 8 层反哺前面各层时的闸门。

## 边界结论

1. **自我改进只能自动提出 diff，不能默认自动应用 diff。**
2. **低风险 memory/context 整理可以自动化，但仍需 provenance、版本、抽样 eval 和 rollback。**
3. **skill、tool、harness、router 更新影响 runtime 行为，至少需要 sandbox、regression 和权限检查。**
4. **eval、reward、log、permission、release gate 是控制面，默认高风险，因为它们会改变“谁来判断改动好不好”。**
5. **training data、fine-tune、adapter、weights 是模型面，必须用 hold-out、lineage、污染检查和 release gate。**
6. **change-risk budget 是 self-improvement 的速率限制器：事故、回滚、false promote 和 gate debt 上升时，自动改动额度下降。**

## 工程模板

每个 proposal 至少包含：

| 字段 | 说明 |
|---|---|
| Proposal id | self-improvement run / dream cycle / agent run id |
| Target layer | 2/4/5/6/7/8 中的主目标 |
| Artifact identity | memory key、prompt hash、skill package、tool schema、harness image、eval set、model snapshot |
| Evidence | 触发 trace、failure taxonomy、eval result、用户反馈、incident 或 product outcome |
| Risk score | 影响面、可逆性、权限、数据权利、security、eval/control-plane touch、用户影响 |
| Required checks | regression、hold-out、permission、lineage、security、contract、canary |
| Decision | auto-apply、sandbox、canary、human review、hold、rollback、reject |
| Budget record | 消耗额度、owner、expiry、monitor、closure evidence |

## Open Questions

- 自我改进系统能否可靠区分“提升能力”和“提升通过 gate 的能力”？目前仍需要 hold-out、人类校准和控制面隔离。
- 对 weight-level self-adaptation，rollback 可能不是 revert 一个文件，而是 route around、replace snapshot 或重新训练；需要更强模型版本治理。
- 对多 agent 自我改进，哪个 agent 有 authority 修改共享 skill、memory、eval 或 policy，仍需要 identity/delegation 和 ownership 约束。

## 回填位置

- [[domains/AI知识体系]] 第 8 层新增 self-improvement gate / change-risk budget。
- [[concepts/Dream与SelfImprovement工程原语]] 增加 gate 作为 proposed diff 后的必经边界。
- [[concepts/ModelReleaseRollbackGate边界]] 增加自我改进变更的特化入口。
- [[concepts/RewardHackingEvalOverfitting边界]] 增加 gate tampering / control-plane self-edit 风险。

## 结论

本轮把第 8 层从“反馈环”推进到“受控反馈环”：系统可以从失败中生成改动，但必须先证明这次改动属于哪个层级、有什么证据、风险是否可预算、坏了怎么回退、由谁负责。这样自我改进才能反哺第 2/4/5/6/7 层，而不是绕过它们。

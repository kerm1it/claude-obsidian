---
address: c-000587
type: review
title: "Review: AI知识体系稳定 v1 结构验收"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - knowledge-system
  - review
  - stable-v1
status: complete
related:
  - "[[domains/AI知识体系]]"
  - "[[learning/AI体系学习路线]]"
  - "[[concepts/AI系统生成链]]"
  - "[[concepts/ProductFeedbackClosureActionability边界]]"
  - "[[concepts/SelfImprovementGateChangeRiskBudget边界]]"
  - "[[concepts/MemorySkillGovernanceDrift边界]]"
sources:
  - "[[Research: AI知识体系总览]]"
  - "[[Research: 微调 vs RAG vs 上下文工程]]"
  - "[[Research: Agent harness 与 trace eval]]"
  - "[[Research: Dream 与 self-improvement 工程原语]]"
  - "[[Research: Data flywheel feedback loop 边界]]"
  - "[[Research: Product feedback closure data flywheel actionability 边界]]"
  - "[[Research: Self-improvement gate change-risk budget 边界]]"
  - "[[Research: Memory skill governance drift 边界]]"
---

# Review: AI知识体系稳定 v1 结构验收

结论：**通过**。[[domains/AI知识体系]] 已达到 stable v1：它不是穷尽所有 AI 名词的列表，而是一套能承接新概念的稳定架构。后续不需要继续默认开研究轮；只有遇到具体新概念或真实学习/工程问题时，才按 research loop 单点回填。

## 验收范围

本次验收不新增主题，只检查三件事：

- 8 个顶层是否固定，且新概念不需要新增第 9 层。
- 层级是否串成完整系统链路，而不是孤立分类表。
- 学习路线和 research loop 是否能回答“下一步学什么”和“新概念放哪里”。

## 结构结论

| 检查项 | 结果 | 说明 |
|---|---|---|
| 顶层稳定性 | PASS | 顶层仍是 8 层：基础理论、模型构建、推理能力、上下文知识、Agent 系统、评估可靠性、产品组织、自我改进。 |
| 链路闭合 | PASS | 链路已形成 `1 -> 2 -> 3 -> 4 -> 5 -> 6 -> 7 -> 8 -> 2/4/5/6/7` 的反馈环。 |
| 边界概念 | PASS | 当前“待归类 / 边界概念”为空；最近主题都能稳定归入现有层级。 |
| 用户验收概念 | PASS | 微调、蒸馏、prompt engineering、context engineering、harness、skill、agent、dream、自我进化均有主归属与交叉链接。 |
| 单点研究合约 | PASS | 每轮必须记录定义、问题、主归属、上下游、工程实践、评估方式和过时风险。 |
| 学习路线 | PASS | [[learning/AI体系学习路线]] 已按“先链路、再单点、再实践验证”组织。 |

## 链路解释

稳定 v1 的核心不是 8 个盒子，而是一个 AI 系统生成链：

1. **基础理论层**解释为什么模型能学。
2. **模型构建层**把数据、反馈和目标压进权重。
3. **推理与能力层**把权重变成运行时能力、成本和延迟。
4. **上下文与知识层**把任务现场、外部知识、memory 和 skill 喂给模型。
5. **Agent 系统层**把模型能力接到工具、状态、权限和行动循环。
6. **评估与可靠性层**判断答案、trace、工具动作、数据、证据和风险是否可靠。
7. **产品与组织层**把可靠能力接入真实工作流、责任链、发布门、事故闭环和数据飞轮。
8. **自我改进与前沿层**提出受控改动，经 gate 后反哺模型、上下文、工具、eval 和产品流程。

这条链路已经能解释用户最初列出的名词：微调和蒸馏属于模型构建；prompt/context/RAG/memory/skill 属于上下文与知识；harness/agent/tool use 属于 Agent 系统；eval/benchmark/质量门属于可靠性；dream/self-improvement 属于反馈环。

## 关键闭合点

- [[concepts/ProductFeedbackClosureActionability边界]] 补上第 7 层到第 8 层的行动闭环：反馈必须有 owner、artifact、验证和关闭证据，才能进入自我改进。
- [[concepts/SelfImprovementGateChangeRiskBudget边界]] 防止第 8 层绕过第 6/7 层：自动改 memory、skill、tool、eval、policy 或 weights 时必须有风险预算、证据和回滚。
- [[concepts/MemorySkillGovernanceDrift边界]] 防止第 4 层长期上下文资产污染未来 agent：memory 和 skill 都需要 owner、freshness、permission、eval、quarantine 和 retirement。
- [[concepts/EvalPortfolioMetricHierarchy边界]]、[[concepts/MetricConflictResolution边界]]、[[concepts/EvidenceFreshnessStaleProof边界]] 让第 6 层从“跑 benchmark”升级为可决策的证据系统。
- [[concepts/ModelReleaseRollbackGate边界]]、[[concepts/AISafetyOpsGovernance边界]]、[[concepts/ProductOrganizationLayer边界]] 让第 7 层从“产品想法”升级为组织执行系统。

## 后续规则

稳定 v1 后，默认不再做无尽 research loop。后续只有三类触发：

- 遇到新概念：先放进 8 层之一，若无法归类才进入“待归类 / 边界概念”。
- 遇到真实学习任务：从 [[learning/AI体系学习路线]] 选阶段和实践题，不从热点列表开始。
- 遇到工程/产品问题：按链路定位失败点，再决定是补数据、改 context/RAG/memory/skill、改 harness/tool、补 eval、过 release gate，还是进入 self-improvement。

## 残余边界

- 芯片底层、政策法规、纯数学推导暂不作为主线；它们可以作为交叉链接进入第 1、3、6、7 层。
- 供应商 API、模型名称、benchmark 榜单会快速变化，但它们应替换具体来源页，不改变顶层结构。
- 权重级自我进化仍是高风险前沿主题；在本体系中必须同时经过第 8 层 gate、第 2 层模型构建和第 6/7 层发布证据。

## 最终判定

Stable v1 可以收口。当前体系已经能承担两个核心用途：

- 学习时：看到新知识能判断它属于哪一层、连接哪些上下游、是否值得深学。
- 研究时：每个新主题都有固定回填位置，不需要因为 buzzword 新鲜就扩顶层。

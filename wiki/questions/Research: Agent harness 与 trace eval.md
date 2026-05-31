---
address: c-000200
type: synthesis
title: "Research: Agent harness 与 trace eval"
created: 2026-05-30
updated: 2026-05-30
tags:
  - research
  - ai
  - agents
  - harness
  - evals
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/AgentHarness与TraceEval]]"
  - "[[concepts/Agent评估体系]]"
  - "[[concepts/Eval驱动开发]]"
  - "[[concepts/智能体优先工程]]"
sources:
  - "[[sources/openai-agents-sdk-tracing-2026]]"
  - "[[sources/openai-agents-sdk-running-2026]]"
  - "[[sources/openai-agent-evals-trace-grading-2026]]"
  - "[[sources/anthropic-managed-agents-2026]]"
  - "[[sources/anthropic-effective-harnesses-long-running-agents-2026]]"
  - "[[sources/harness-bench-2026]]"
  - "[[sources/ai-harness-engineering-2026]]"
  - "[[sources/harness-audit-2026]]"
  - "[[sources/openai-agents-sdk-evolution-2026]]"
  - "[[sources/anthropic-demystifying-evals-agents-2026-05-26]]"
  - "[[sources/harness-engineering-openai-2026-02-11]]"
---

# Research: Agent harness 与 trace eval

## Overview

Agent harness 是从“模型会调用工具”到“系统能长期、安全、可观测地行动”的运行时层。Trace eval 则把运行时记录变成评估证据，让团队能判断 agent 的最终结果、过程、成本、权限和恢复能力。

本轮把 harness 主归属放在 [[domains/AI知识体系]] 第 5 层，并把 trace/eval 作为第 5 层到第 6 层的桥。

## Key Findings

- OpenAI Agents SDK 把 agent 运行组织为 agent loop：模型响应、工具调用、handoff、停止条件和最大回合数由 runner 管理。（Source: [[sources/openai-agents-sdk-running-2026]]）
- OpenAI Agents SDK tracing 自动记录 agent run、generation、function、handoff、guardrail 等 span，是把运行时转成 eval/监控素材的标准机制。（Source: [[sources/openai-agents-sdk-tracing-2026]]）
- OpenAI 的 agent eval / trace grading 工作流强调用真实或生成 trace 训练 grader，并按 trace 判断 agent 行为是否满足 rubric。（Source: [[sources/openai-agent-evals-trace-grading-2026]]）
- Anthropic 的 managed agents 经验说明，多 agent 系统的瓶颈在于 orchestration、任务委派、状态共享和自动 verification。（Source: [[sources/anthropic-managed-agents-2026]]）
- Anthropic 的 long-running agent harness 研究把有效 harness 拆成环境、工具、上下文、反馈、恢复、观测等工程要素。（Source: [[sources/anthropic-effective-harnesses-long-running-agents-2026]]）
- Harness-Bench 和 HarnessAudit 都说明同一个模型在不同 harness 中表现会显著变化，因此 benchmark 不能只看模型名，也要记录 harness 条件。（Source: [[sources/harness-bench-2026]], [[sources/harness-audit-2026]]）
- AI Harness Engineering 将 harness 作为系统性工程对象：环境、工具、记忆、控制流和评价共同影响 agent 性能。（Source: [[sources/ai-harness-engineering-2026]]）

## Stable Definition

**Harness = agent runtime.**

它负责让 agent 在边界内行动：拿到正确上下文，调用授权工具，维护状态，处理错误，产出 trace，并在必要时进入 sandbox 或 human approval。

**Trace eval = runtime audit.**

它不只问最终回答对不对，而是问“agent 如何到达结果、过程是否可靠、代价是否可接受、风险是否被控制”。

## 上下游

| 方向 | 内容 |
|---|---|
| 上游 | 模型能力、上下文、memory、tools、任务 spec、权限策略 |
| 主归属 | 第 5 层 Agent 系统层 |
| 交叉 | 第 6 层评估与可靠性层 |
| 下游 | 产品 agent、软件工厂、研究 agent、computer-use agent |
| 反哺 | trace → eval → failure taxonomy → prompt/tool/memory/model 改进 |

## 工程实践

1. 定义 runner loop：最大回合数、停止条件、handoff、失败恢复。
2. 定义 tool registry：schema、权限、超时、错误语义、审计日志。
3. 定义 workspace：文件、网络、命令、sandbox、可回滚边界。
4. 定义 state/session：当前任务状态、短期记忆、恢复点。
5. 记录 trace：agent、generation、tool、handoff、guardrail、error span。
6. 建 eval harness：批量运行任务、读取 trace、评分、生成 regression report。

## Open Questions

- Trace schema 是否会在 OpenAI、Anthropic、LangSmith、OpenTelemetry 之间收敛。
- Eval 应优先评分最终状态还是 trace 路径；不同 agent 类型的权重不同。
- 托管 agent 能吸收多少本地 harness 工作，哪些仍必须由产品团队控制。

## Filed Result

本轮归档为 [[concepts/AgentHarness与TraceEval]]，并回填 [[domains/AI知识体系]] 第 5 层与第 6 层连接；下一步继续研究 Dream / self-improvement 的工程原语。

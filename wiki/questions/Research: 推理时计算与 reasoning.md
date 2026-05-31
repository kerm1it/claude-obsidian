---
address: c-000227
type: synthesis
title: "Research: 推理时计算与 reasoning"
created: 2026-05-30
updated: 2026-05-30
tags:
  - research
  - ai
  - reasoning
  - test-time-compute
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/TestTimeCompute]]"
  - "[[concepts/AdaptiveThinking]]"
  - "[[concepts/EffortDial]]"
  - "[[concepts/TaskBudgets]]"
  - "[[concepts/AgentHarness与TraceEval]]"
sources:
  - "[[sources/openai-learning-to-reason-2024]]"
  - "[[sources/anthropic-extended-thinking-docs-2026]]"
  - "[[sources/scaling-llm-test-time-compute-2024]]"
  - "[[sources/chain-of-thought-2022]]"
  - "[[sources/self-consistency-2022]]"
  - "[[sources/tree-of-thoughts-2023]]"
  - "[[sources/openai-process-supervision-2023]]"
  - "[[sources/openai-cot-monitorability-2025]]"
  - "[[sources/the-thinking-lever-2026-05-11]]"
---

# Research: 推理时计算与 reasoning

## Overview

推理时计算是第 3 层“推理与能力层”的核心机制：模型权重不变时，通过更多运行时 token、采样、搜索、verifier、reranker、tool loop 和 effort/budget 控制换取更高质量或更高可靠性。它不是 prompt engineering，也不是 agent harness；它是模型运行时把计算转化为能力的桥梁，并通过第 5 层 harness 进入行动系统。

稳定链路：`模型权重 → reasoning policy / effort → search or thinking or sampling → tool/result feedback → verifier/eval → final answer/action`。

## Key Findings

- OpenAI o1 把 reasoning 模型描述为通过强化学习学习使用 chain of thought，并显示 performance 随 train-time compute 与 test-time compute 提升。（Source: [[sources/openai-learning-to-reason-2024]]）
- Anthropic extended/adaptive thinking 把推理时计算暴露为 API 控制面：thinking budget、adaptive thinking、effort，以及与 tool use 的连续 turn 约束。（Source: [[sources/anthropic-extended-thinking-docs-2026]]）
- Scaling LLM Test-Time Compute 论文说明 test-time compute 的收益依赖题目难度；compute-optimal 分配比 naive best-of-N 更高效，并可在特定条件下让小模型超过大模型。（Source: [[sources/scaling-llm-test-time-compute-2024]]）
- Chain-of-Thought 证明“写出中间推理步骤”可以提升大模型在算术、常识和符号任务上的表现。（Source: [[sources/chain-of-thought-2022]]）
- Self-consistency 用多条推理路径采样和答案一致性替代 greedy decoding，是早期 test-time scaling 的典型策略。（Source: [[sources/self-consistency-2022]]）
- Tree of Thoughts 把单线 CoT 扩展为搜索树，适合需要探索、lookahead、backtracking 的任务。（Source: [[sources/tree-of-thoughts-2023]]）
- Process supervision 用逐步奖励模型选择推理过程，而不仅仅奖励最终答案，是 verifier / reranker 与 reasoning 连接的关键证据。（Source: [[sources/openai-process-supervision-2023]]）
- CoT monitorability 把 reasoning trace 接到可靠性层：更长 thinking 往往更可监控，但 CoT 可监控性必须被评估和维护。（Source: [[sources/openai-cot-monitorability-2025]]）

## Stable Boundary

| 概念 | 主职责 | 归属 |
|---|---|---|
| Reasoning | 模型运行时的推理过程和策略选择 | 3. 推理与能力层 |
| Test-time compute | 在推理阶段分配更多计算来换质量、可靠性或可监控性 | 3. 推理与能力层 |
| Prompt / context | 提供任务信息和约束，不等于推理能力本身 | 4. 上下文与知识层 |
| Agent loop | 把推理和 tool/action 组织成多步环境交互 | 5. Agent 系统层 |
| Eval / verifier | 判断推理过程、最终答案、工具动作是否可靠 | 6. 评估与可靠性层 |

## 策略谱系

| 策略 | 多花在哪里 | 适合任务 | 风险 |
|---|---|---|---|
| CoT / extended thinking | 单条推理链 token | 中等复杂推理 | 冗长、伪解释 |
| Self-consistency | 多条推理路径采样 | 有唯一答案的推理题 | 成本线性增长 |
| Best-of-N / rerank | 多候选生成 + scorer | 数学、代码、选择题 | scorer 过拟合 |
| Tree/search | 搜索树、lookahead、backtracking | 规划、组合搜索 | 状态空间爆炸 |
| Tool-interleaved thinking | tool call 之间的推理 | agentic coding、research、computer use | 轨迹变长、缓存/状态复杂 |
| Adaptive effort | 按任务难度动态分配 | 混合难度工作流 | 需要 workload eval 校准 |

## 与 Agent Loop 的连接

推理时计算进入 agent 系统后，单位不再只是“答案 token”，而是完整 trace：

1. 模型判断任务难度和不确定性。
2. effort / budget 决定本轮思考、采样或工具使用规模。
3. harness 执行 tool call，并把 tool result 送回同一行动轨迹。
4. 模型继续 reasoning，必要时改计划、重试、回滚或求证。
5. eval / verifier 检查最终状态、过程 trace、成本和安全边界。

因此 TTC 在 agent 中的指标必须包含：成功率、turn 数、tool-call 正确率、成本、延迟、trace 可监控性和失败恢复能力。

## Open Questions

- CoT 可监控性是否会随着更强 RL、蒸馏或隐藏推理而下降。
- 不同任务上 effort 的最优点如何自动选择，而不是靠人工调参。
- 推理时计算、上下文长度、tool use 和 memory 之间的预算如何统一优化。

## Filed Result

本轮更新 [[concepts/TestTimeCompute]]，并回填 [[domains/AI知识体系]] 第 3 层。推理时计算的稳定定位：它是第 3 层运行时能力机制，通过第 5 层 harness 变成 agent 行动，通过第 6 层 eval / verifier / monitorability 进入可靠性闭环。

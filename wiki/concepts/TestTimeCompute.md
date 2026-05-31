---
type: concept
address: c-000055
title: "Test-Time Compute（推理时计算扩展）"
created: 2026-05-11
updated: 2026-05-30
tags:
  - test-time-compute
  - scaling
  - reasoning
  - anthropic
status: active
related:
  - "[[concepts/AdaptiveThinking]]"
  - "[[concepts/EffortDial]]"
  - "[[concepts/ScalingLaws]]"
  - "[[concepts/AgentHarness与TraceEval]]"
  - "[[concepts/ReasoningEvalVerifier边界]]"
  - "[[concepts/ModelRoutingMixture边界]]"
  - "[[sources/the-thinking-lever-2026-05-11]]"
sources:
  - "[[Research: 推理时计算与 reasoning]]"
  - "[[sources/openai-learning-to-reason-2024]]"
  - "[[sources/anthropic-extended-thinking-docs-2026]]"
  - "[[sources/scaling-llm-test-time-compute-2024]]"
  - "[[sources/chain-of-thought-2022]]"
  - "[[sources/self-consistency-2022]]"
  - "[[sources/tree-of-thoughts-2023]]"
  - "[[sources/openai-process-supervision-2023]]"
  - "[[sources/openai-cot-monitorability-2025]]"
  - "[[Research: Reasoning eval verifier 边界]]"
---

# Test-Time Compute（推理时计算扩展）

**来源**：[[sources/the-thinking-lever-2026-05-11]]，[[people/MattBleifer]]（Anthropic）

---

## 是什么

Test-time compute 是继**训练时扩展**（更大模型、更多数据、更长训练）之后的第二条智能扩展路径：**让模型在推理时花更多时间/token 来解决问题**。

两条路径都能提升性能，但切入角度不同：
- 训练时扩展 → 更聪明的模型
- 推理时扩展 → 同一模型在同一问题上做得更好

在 [[domains/AI知识体系]] 中主归属：**3. 推理与能力层**。它消费模型权重、推理预算和任务状态，输出更强的 reasoning、planning、tool-use 决策和可监控 trace。

---

## 实验证据

同一 Opus 4.7 模型，在交通灯模拟任务上：

| Effort 级别 | 时间倍数 | Token 倍数 | 结果质量 |
|-------------|---------|-----------|---------|
| Low | 1× | 1×（~4600 tokens） | 基础，红绿灯放路中间 |
| High | 2× | 2× | 更好，多车型，智能驾驶模型 |
| Max | 10× | 10× | 最佳图形，最真实驾驶模式 |

适用范围：不只是软件工程，还包括 agentic search、computer use、PhD 级学术推理等所有知识工作领域。

---

## Claude 的三类推理时 Token

- **Thinking tokens**：内部推理、chain-of-thought、草稿本
- **Tool call tokens**：与外部环境交互（搜索、文件读写等）
- **Text tokens**：与用户沟通（进度更新、最终回答）

→ 详见 [[concepts/AdaptiveThinking]]

---

## 稳定策略谱系

| 策略 | 多花在哪里 | 代表机制 | 适合任务 |
|---|---|---|---|
| 单线推理 | 一条 reasoning trace | Chain-of-Thought、extended thinking | 中等复杂推理 |
| 多路径采样 | 多条 reasoning traces | Self-consistency、majority vote | 有唯一答案的推理题 |
| 搜索与回溯 | 状态树 / 候选 thought | Tree of Thoughts | 规划、组合搜索 |
| Verifier / reranker | 多候选 + scoring | outcome verifier、process verifier、learned scorer | 数学、代码、严格验证任务 |
| Tool-interleaved reasoning | tool call 之间继续推理 | interleaved thinking、agent loop | coding、research、computer use |
| Adaptive effort | 按难度动态分配预算 | effort、adaptive thinking | 混合难度工作流 |

## 与相邻层的边界

| 概念 | 区别 |
|---|---|
| Prompt engineering | prompt 提供指令；test-time compute 分配运行时计算 |
| Context engineering | context 管理输入信息；TTC 决定如何处理这些信息 |
| Agent harness | harness 管理 loop、tools、state；TTC 决定每一步推理投入 |
| Eval | eval 衡量 TTC 是否真的提高成功率、可靠性和可监控性 |
| Model routing | routing 选择哪个模型/effort/cascade 承载任务；TTC 是被选择路径内部花多少计算 |
| Fine-tuning | fine-tuning 改权重；TTC 不改权重，改推理时策略和预算 |

## 与 Agent Loop 的连接

在 agent 中，推理时计算不只影响最终答案，还影响整个 trace：

1. 模型根据任务难度、不确定性和工具结果决定是否继续思考。
2. Effort / budget 控制 thinking、tool use、采样或搜索规模。
3. Harness 执行工具并把结果送回同一轨迹。
4. 模型用新的 observation 调整计划、重试或回滚。
5. Eval / monitor 消费 trace、最终状态、成本和延迟，判断本轮计算是否值得。

稳定结论：**第 3 层 TTC 通过第 5 层 harness 变成行动，通过第 6 层 eval 变成可控优化**。

## 与 Reasoning Verifier 的接口

[[concepts/ReasoningEvalVerifier边界]] 是 TTC 进入第 6 层的主要接口：

- outcome verifier 选择最终答案或最终状态。
- process verifier / PRM 评价中间步骤是否推进解题。
- trace grader 评价 agent 轨迹、工具调用和恢复路径。
- verifier 的成本、延迟、校准和 reward hacking 风险必须纳入 TTC 的收益曲线。

## 与 Model Routing 的接口

[[concepts/ModelRoutingMixture边界]] 把 TTC 从单模型预算扩展成多模型预算：

- 简单任务可以路由到小模型或低 effort。
- 不确定或高风险任务可以升级到强模型、高 effort、verifier 或人工门。
- cheap-first cascade 本质是先花小预算，再根据置信/验证结果决定是否追加预算。
- parallel ensemble / MoA 是高成本的 TTC 扩展，适合高价值开放任务，不适合默认路径。

## 评估方式

- 成功率：pass@1、pass@k、pass^k、任务完成率。
- 成本曲线：token、时间、API 成本、tool call 数。
- 边际收益：effort 从 low 到 high 是否仍有收益。
- 可靠性：多次运行的方差、失败恢复、回归任务。
- 可监控性：CoT / trace 是否能帮助发现错误、欺骗、reward hacking 或偏差。
- 产品约束：延迟是否满足用户体验，成本是否能规模化。

## 过时风险

- “chain-of-thought”外显形式可能随平台隐藏推理而变化，但“推理时预算换质量”的结构稳定。
- 简单 CoT prompt 会被 reasoning model 内化；仍需要 effort、budget、verifier、trace eval 来控制系统。
- Test-time compute 容易带来成本和延迟膨胀，必须用任务级 eval 找拐点。
- CoT 可监控性不是保证；蒸馏、RL 或隐藏推理可能改变它的可靠性。

---

## 关联

- [[concepts/AdaptiveThinking]] — token 分配的自适应机制
- [[concepts/EffortDial]] — 用户控制推理时计算的接口
- [[concepts/ScalingLaws]] — 训练时扩展律（对比视角）
- [[concepts/AgentHarness与TraceEval]] — TTC 在 agent 中通过 trace/eval 被约束
- [[concepts/ReasoningEvalVerifier边界]] — verifier / grader 如何把 reasoning 变成可评分、可选择和可训练的信号
- [[concepts/ModelRoutingMixture边界]] — 多模型场景下如何选择模型、effort、cascade 或 ensemble
- [[Research: 推理时计算与 reasoning]]

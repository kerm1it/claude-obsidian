---
address: c-000261
type: concept
title: "Reasoning Eval / Verifier 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - reasoning
  - evals
  - verifier
  - reward-models
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/TestTimeCompute]]"
  - "[[concepts/AgentHarness与TraceEval]]"
  - "[[concepts/ModelRoutingMixture边界]]"
  - "[[concepts/RewardHackingEvalOverfitting边界]]"
  - "[[concepts/Agent评估体系]]"
  - "[[concepts/Eval驱动开发]]"
  - "[[concepts/LLMJudgeAIFeedbackCalibration边界]]"
sources:
  - "[[Research: Reasoning eval verifier 边界]]"
  - "[[sources/openai-math-verifiers-2021]]"
  - "[[sources/lets-verify-step-by-step-2023]]"
  - "[[sources/openai-process-supervision-2023]]"
  - "[[sources/openai-prover-verifier-games-2024]]"
  - "[[sources/openai-graders-docs-2026]]"
  - "[[sources/g-eval-2023]]"
  - "[[sources/mt-bench-chatbot-arena-llm-as-judge-2023]]"
  - "[[sources/openai-agent-evals-trace-grading-2026]]"
  - "[[sources/rewardbench-2024]]"
  - "[[sources/rewarding-progress-process-verifiers-2024]]"
  - "[[sources/processbench-2024]]"
  - "[[sources/process-reward-models-that-think-2025]]"
  - "[[sources/openai-cot-monitorability-2025]]"
---

# Reasoning Eval / Verifier 边界

Reasoning eval / verifier 是**评估与可靠性层**对推理过程、候选答案、agent trace 或中间步骤进行评分、选择、监控和归因的机制。它不负责“产生推理”，而负责判断推理是否可靠、是否值得继续搜索、是否能进入产品或训练闭环。

主归属：**6. 评估与可靠性层**。

稳定链路：

`模型输出 / reasoning trace / tool trace → verifier / grader / monitor → score / label / failure reason → rerank / gate / train / improve`

## 解决的问题

- 复杂推理常常“一步错，全局错”；只看最终答案会漏掉错误来源。
- 多路径采样、搜索和 agent loop 会产生许多候选，需要选择、剪枝和归因。
- Agent 会调用工具并改变环境，正确性不只在文本答案里，也在 trace 和最终状态里。
- 自我改进如果没有可靠 verifier，会把失败、偏见或 reward hack 固化进记忆、skill、eval 或训练数据。

## 类型边界

| 类型 | 评估对象 | 典型输出 | 主用途 |
|---|---|---|---|
| Outcome verifier / ORM | 最终答案或最终环境状态 | 正确/错误、分数、偏好 | final-answer rerank、回归 eval、RLHF/RFT reward |
| Process verifier / PRM | 推理链中的每一步 | step-level validity、错误位置、progress score | 搜索剪枝、process supervision、dense reward |
| Trace grader | agent 全量 trajectory | rubric label、工具错误、恢复失败、成本问题 | agent eval、regression、orchestration 改进 |
| CoT monitor | 暴露的 reasoning / thinking trace | misbehavior signal、风险信号 | 安全监控、欺骗/投机行为发现 |
| Reward model | 偏好或过程标签训练出的 scorer | reward / ranking | 对齐训练、DPO/RLHF/RFT、best-of-N 选择 |
| Eval harness | 批量运行任务和 graders 的基础设施 | suite score、diff、transcript | 回归、上线质量门、版本比较 |

## 与相邻概念的区别

| 概念 | 边界 |
|---|---|
| [[concepts/TestTimeCompute]] | TTC 分配 thinking、采样、搜索和工具回合；verifier 判断哪些路径更可靠 |
| [[concepts/AgentHarness与TraceEval]] | harness 产生 trace；trace grader 消费 trace 并输出质量信号 |
| Prompt / context engineering | prompt/context 提供任务信息；verifier 评估结果和过程是否符合目标 |
| Fine-tuning / RLHF / RFT | 训练改权重；verifier/reward model 提供训练信号或训练后的评估门 |
| Benchmark | benchmark 是任务集；verifier/grader 是对单个样本或 trace 的评分逻辑 |
| Model routing | router 选择执行路径；verifier/grader 为 router 提供质量、置信、升级和失败归因信号 |
| Reward hacking / eval overfitting | verifier 是质量门；reward hacking 是系统学会钻质量门空子 |
| [[concepts/LLMJudgeAIFeedbackCalibration边界]] | LLM judge 是 verifier/grader 的一类实现；本页说明 verifier 在系统中的位置，LLM judge calibration 说明这类 grader 如何被校准和防偏 |

## 上下游

| 方向 | 内容 |
|---|---|
| 上游输入 | 模型候选答案、reasoning trace、工具调用、环境状态、参考答案、rubric、人工标签 |
| 下游输出 | 分数、标签、错误步骤、失败归因、可读性信号、训练 reward、上线 gate |
| 被谁使用 | TTC search/rerank、agent eval、model optimization、RFT/RLHF、self-improvement |
| 反哺对象 | 第 2 层训练数据/奖励模型，第 3 层 model routing，第 4 层 prompt/context/memory，第 5 层 harness/tool，第 8 层 dream/self-improvement |

## 工程实践

1. 先建立任务级 outcome eval：参考答案、单元测试、状态检查或人工 rubric。
2. 当失败发生在推理过程或 agent 路径中，再加 process / trace eval。
3. 对可确定任务优先用代码 grader；开放任务才用 LLM grader，并用人工样本校准。
4. 对多候选 reasoning 使用 verifier 做 best-of-N、rerank 或 search pruning。
5. 对 model router 使用 verifier/calibration 检查是否错把难题交给弱模型。
6. 对 agent 读取 transcript/trace，检查工具选择、参数、恢复路径、成本和最终状态。
7. 对训练闭环保留 hold-out eval，防止 reward model 过拟合和 benchmark leakage。
8. 对 grader / reward model 做 adversarial eval，专门寻找 reward hacking、grader hacking 和 leakage。

## 评估方式

- 与人工标签一致性：accuracy、F1、precision/recall、inter-rater agreement。
- 校准：高分样本是否真的高成功率，低分样本是否能解释失败。
- 稳定性：模型、prompt、rubric 或 sampling 改变后，grader 是否漂移。
- 鲁棒性：对 adversarial answer、长 trace、无关步骤、投机答案和 reward hacking 的抵抗力。
- 产品指标：成功率提升是否超过 verifier 自身的 token、延迟和成本。
- 归因价值：分数之外，是否能定位是 prompt、tool、memory、model、harness 还是 eval 本身失败。

## 过时风险

- 外显 CoT 可能被平台隐藏或被模型内化；但“过程可评估性”和 trace 监控仍然存在。
- PRM 在数学上效果突出，但跨通用推理、代码、知识型错误和多模态任务的泛化仍需验证。
- LLM-as-judge 容易受位置偏差、提示偏差、模型漂移和同源模型偏见影响，不能无校准使用。
- 过度优化 verifier 会造成 reward hacking：模型学会骗过评分器，而不是解决真实问题。
- Benchmark 会饱和或泄漏；上线前仍要用私有、真实、持续更新的任务集。

## 稳定结论

Reasoning eval / verifier 不是新的顶层。它是第 6 层把第 3 层 reasoning、第 5 层 agent trace、第 2 层训练反馈和第 8 层自我改进串起来的质量门。

[[concepts/RewardHackingEvalOverfitting边界]] 是它的主要失效模式：当 verifier、reward、benchmark 或 grader 被优化压力利用时，分数会脱离真实目标。

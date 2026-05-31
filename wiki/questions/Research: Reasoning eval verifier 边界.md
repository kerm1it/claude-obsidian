---
address: c-000262
type: synthesis
title: "Research: Reasoning eval verifier 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - research
  - ai
  - reasoning
  - evals
  - verifier
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/ReasoningEvalVerifier边界]]"
  - "[[concepts/TestTimeCompute]]"
  - "[[concepts/AgentHarness与TraceEval]]"
  - "[[concepts/Agent评估体系]]"
sources:
  - "[[sources/openai-math-verifiers-2021]]"
  - "[[sources/lets-verify-step-by-step-2023]]"
  - "[[sources/openai-process-supervision-2023]]"
  - "[[sources/openai-prover-verifier-games-2024]]"
  - "[[sources/openai-graders-docs-2026]]"
  - "[[sources/openai-agent-evals-trace-grading-2026]]"
  - "[[sources/anthropic-demystifying-evals-agents-2026-05-26]]"
  - "[[sources/rewardbench-2024]]"
  - "[[sources/rewarding-progress-process-verifiers-2024]]"
  - "[[sources/processbench-2024]]"
  - "[[sources/process-reward-models-that-think-2025]]"
  - "[[sources/openai-cot-monitorability-2025]]"
---

# Research: Reasoning eval verifier 边界

## Overview

Reasoning eval / verifier 是第 6 层评估与可靠性机制：它消费第 3 层 reasoning 输出、第 5 层 agent trace 和第 2 层训练信号，产出分数、标签、错误定位、rerank 决策和质量门。它不是 prompt、不是 harness、也不是新顶层，而是 reasoning、agent、训练和 self-improvement 之间的可靠性接口。

稳定链路：`reasoning candidates / trace → outcome verifier or process verifier or trace grader → score / label / failure reason → rerank / gate / train / improve`。

## Key Findings

- OpenAI 2021 年的 math verifier 工作把“生成多个候选解，再由 verifier 选择”确立为推理时计算的一种基础模式；verification 利用了“验证通常比生成简单”的结构。（Source: [[sources/openai-math-verifiers-2021]]）
- Let’s Verify Step by Step 将 outcome supervision 与 process supervision 区分开：前者只看最终结果，后者给每个中间步骤反馈；在 MATH 子集上，process-supervised reward model 明显优于 outcome-supervised reward model。（Source: [[sources/lets-verify-step-by-step-2023]]）
- Process supervision 同时是第 6 层 eval 机制和第 2 层训练信号：PRM 可以用于 best-of-N/search，也可以作为 dense reward 参与训练。（Source: [[sources/openai-process-supervision-2023]]）
- Prover-verifier games 指出“答案正确”不等于“容易验证”：只优化正确率可能损害可读性；把强模型输出训练成弱 verifier 和人类更容易检查的形式，是可靠性目标的一部分。（Source: [[sources/openai-prover-verifier-games-2024]]）
- OpenAI graders 文档把 grader 明确定义为 eval 和 fine-tuning 的评分组件，可做字符串检查、文本相似度、模型评分和 Python 执行，也能组合成 multigrader。（Source: [[sources/openai-graders-docs-2026]]）
- Trace grading 将 agent eval 从最终回答扩展到完整轨迹：评估决策、工具调用、reasoning steps、恢复路径、成本和最终状态。（Source: [[sources/openai-agent-evals-trace-grading-2026]]）
- Anthropic agent eval 经验强调要读取 transcript：否则无法判断是 agent 真失败、grader 错判，还是 eval 约束写错。（Source: [[sources/anthropic-demystifying-evals-agents-2026-05-26]]）
- RewardBench 说明 reward model 本身也需要被评估；reward model 会在 chat、reasoning、safety 和 out-of-distribution 查询上暴露偏好和能力边界。（Source: [[sources/rewardbench-2024]]）
- Rewarding Progress 提出 process reward 不应只判断局部步骤对错，而应衡量这一步是否提高未来得到正确答案的概率；这把 PRM 接到 test-time search 和 online RL。（Source: [[sources/rewarding-progress-process-verifiers-2024]]）
- ProcessBench 与 ThinkPRM 一起说明：通用 PRM 泛化仍困难，critic model / generative verifier / long-CoT verifier 是正在演化的方向，但需要独立 benchmark 和 hold-out eval。（Source: [[sources/processbench-2024]]、[[sources/process-reward-models-that-think-2025]]）

## Classification

| 概念 | 主归属 | 上游 | 下游 |
|---|---|---|---|
| Outcome verifier / ORM | 6. 评估与可靠性层 | 最终答案、参考答案、状态 | best-of-N、回归 eval、reward |
| Process verifier / PRM | 6. 评估与可靠性层 | 中间步骤、step labels、trace | search pruning、process supervision、dense reward |
| Trace grader | 6. 评估与可靠性层 | agent transcript、tool calls、环境状态 | agent regression、harness 改进 |
| Reward model | 6. 评估与可靠性层 | 偏好数据、rubric、过程标签 | RLHF/RFT/DPO、rerank、质量门 |
| Eval harness | 6. 评估与可靠性层 | tasks、graders、环境、模型版本 | suite score、diff、上线决策 |

交叉链接：
- 第 3 层：TTC/search/rerank 需要 verifier 选择路径。
- 第 5 层：agent harness 产出 trace，trace grader 消费 trace。
- 第 2 层：reward model / grader 可成为 RFT/RLHF 的训练信号。
- 第 8 层：self-improvement 使用 verifier 作为防止坏经验固化的质量门。

## Engineering Pattern

1. 先写 outcome eval：测试、状态检查、参考答案或明确 rubric。
2. 发现失败来自路径或中间步骤时，再加 process / trace eval。
3. 能用确定性 grader 就不用 LLM judge；必须用 LLM judge 时，用人工样本校准。
4. 对多候选推理，用 verifier 做 best-of-N、rerank 或 search pruning。
5. 对 agent eval，保存 transcript/trace，手动抽查 grader 是否错判。
6. 对训练和 self-improvement，使用 hold-out eval、审计日志和 rollback。

## Contradictions

- Process supervision 在 OpenAI 的 MATH 任务上显著优于 outcome supervision，但 ProcessBench 显示现有 PRM 在更难或更分布外的数学任务上泛化不足。结论：PRM 是强方向，但不能假设一个数学 PRM 自动泛化到所有 reasoning。
- LLM-as-judge / generative verifier 可以减少 step-level 人工标签需求，但也引入 judge drift、提示敏感性和同源模型偏见。结论：LLM judge 必须被当作待评估系统，而不是绝对裁判。

## Open Questions

- 通用 reasoning verifier 能否跨数学、代码、科学、法律、长程 agent 任务稳定泛化。
- 当平台隐藏 CoT 时，哪些 trace signal 可以替代过程监督。
- Verifier 的成本、延迟和可靠性如何在产品 SLO 下共同优化。
- 自我改进闭环中，如何防止系统同时优化 generator 和 verifier 后出现协同 reward hacking。

## Filing

本轮归档为 [[concepts/ReasoningEvalVerifier边界]]，并回填 [[domains/AI知识体系]]。结论：reasoning eval / verifier 主属第 6 层，是第 3 层 reasoning、第 5 层 agent trace、第 2 层训练和第 8 层 self-improvement 的质量接口，不新增顶层。

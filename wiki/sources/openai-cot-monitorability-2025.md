---
address: c-000235
type: source
title: "Evaluating chain-of-thought monitorability"
source_url: https://openai.com/index/evaluating-chain-of-thought-monitorability/
source_type: research-blog
author: "OpenAI"
published: 2025-12-18
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - reasoning
  - monitorability
  - evals
status: active
related:
  - "[[concepts/TestTimeCompute]]"
  - "[[concepts/AgentHarness与TraceEval]]"
  - "[[concepts/ReasoningEvalVerifier边界]]"
  - "[[concepts/RewardHackingEvalOverfitting边界]]"
---

# Evaluating chain-of-thought monitorability

**来源**：OpenAI Research
**URL**：https://openai.com/index/evaluating-chain-of-thought-monitorability/

## 摘要

OpenAI 提出 chain-of-thought monitorability 的评估框架，研究它如何随 test-time compute、reinforcement learning 和 pretraining scale 变化。文章把 CoT 从能力机制连接到可靠性控制层。

## 关键贡献

- Monitorability 是 monitor 预测 agent 行为相关属性的能力。
- CoT 可能比只看 actions / final outputs 更适合发现某些 misbehavior。
- 更长 thinking 往往更可监控，但 monitorability 不是完美性质，需要持续评估。
- 文章提出 intervention、process、outcome-property 三类 eval。
- Reasoning effort、model size 和可监控性之间存在成本权衡。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：3. 推理与能力层、5. Agent 系统层
- 作用：把推理过程本身纳入 eval / monitoring 范围。

## 关联

- [[concepts/TestTimeCompute]]
- [[concepts/AgentHarness与TraceEval]]
- [[concepts/ReasoningEvalVerifier边界]]
- [[concepts/RewardHackingEvalOverfitting边界]]
- [[Research: 推理时计算与 reasoning]]
- [[Research: Reasoning eval verifier 边界]]

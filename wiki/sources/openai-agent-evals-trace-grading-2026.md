---
address: c-000203
type: source
title: "Agent evals and trace grading"
source_url: https://developers.openai.com/api/docs/guides/agent-evals
source_type: documentation
author: "OpenAI"
published: 2026-05-30
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - agents
  - evals
  - trace-grading
status: active
related:
  - "[[concepts/AgentHarness与TraceEval]]"
  - "[[concepts/Eval驱动开发]]"
  - "[[concepts/ReasoningEvalVerifier边界]]"
---

# Agent evals and trace grading

**来源**：OpenAI API documentation
**URL**：https://developers.openai.com/api/docs/guides/agent-evals
**相关**：https://developers.openai.com/api/docs/guides/trace-grading

## 摘要

OpenAI 的 agent evals 和 trace grading 文档把 agent 评估从“最终回答评分”推进到“按完整运行 trace 评分”。Trace 可以来自生产日志，也可以通过合成任务生成，再用于训练或校准 grader。

## 关键贡献

- Agent evals 使用任务、trace、grader 和 rubric 来判断多步 agent 是否可靠完成目标。
- Trace grading 适合评估工具使用、推理过程、恢复路径、风险行为和最终状态。
- 这些文档把 harness 与 eval 连接起来：没有 trace，agent eval 很难定位失败原因。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：5. Agent 系统层
- 作用：说明 trace 是第 5 层运行时产物，也是第 6 层评估输入。

## 关联

- [[concepts/AgentHarness与TraceEval]]
- [[concepts/Eval驱动开发]]
- [[concepts/ReasoningEvalVerifier边界]]
- [[Research: Agent harness 与 trace eval]]
- [[Research: Reasoning eval verifier 边界]]

---
address: c-000266
type: source
title: "Graders"
source_url: https://developers.openai.com/api/docs/guides/graders
source_type: documentation
author: "OpenAI"
published: 2026-05-30
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - evals
  - graders
  - fine-tuning
status: active
related:
  - "[[concepts/ReasoningEvalVerifier边界]]"
  - "[[concepts/Agent评估体系]]"
  - "[[concepts/Eval驱动开发]]"
  - "[[concepts/LLMJudgeAIFeedbackCalibration边界]]"
  - "[[concepts/JudgeDriftGraderObservability边界]]"
---

# Graders

**来源**：OpenAI API documentation
**URL**：https://developers.openai.com/api/docs/guides/graders

## 摘要

OpenAI Graders 文档定义了可用于 eval 和 fine-tuning 的评分组件。Grader 比较 reference answer 与 model output，并返回 0 到 1 的评分；也支持组合多个 grader。

## 关键贡献

- Grader 类型包括 string check、text similarity、score model grader 和 Python code execution。
- Tool calling 行为可以分别评分 tool name 和 arguments。
- Multigrader 可组合多个评分器，用于更复杂的 eval 或 reinforcement fine-tuning。
- Grader 是 eval harness 与训练反馈之间的稳定接口。
- Model grader 也可能被 grader hacking，需要用 expert human eval 和 hold-out 任务校准。
- Grader 上线后还需要监控版本、prompt、schema、分数分布和 human agreement，避免 judge drift 污染 release 或 fine-tuning feedback。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：2. 模型构建层、5. Agent 系统层
- 作用：提供工程上可实施的 verifier / grader 接口。

## 关联

- [[concepts/ReasoningEvalVerifier边界]]
- [[concepts/LLMJudgeAIFeedbackCalibration边界]]
- [[concepts/JudgeDriftGraderObservability边界]]
- [[concepts/Agent评估体系]]
- [[Research: Reasoning eval verifier 边界]]

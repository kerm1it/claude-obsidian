---
address: c-000228
type: source
title: "Learning to reason with LLMs"
source_url: https://openai.com/index/learning-to-reason-with-llms/
source_type: research-blog
author: "OpenAI"
published: 2024-09-12
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - reasoning
  - test-time-compute
  - openai
status: active
related:
  - "[[concepts/TestTimeCompute]]"
---

# Learning to reason with LLMs

**来源**：OpenAI Research
**URL**：https://openai.com/index/learning-to-reason-with-llms/

## 摘要

OpenAI 发布 o1-preview 时，将 reasoning 模型描述为会在回答前花时间“思考”的模型。文章强调 o1 通过大规模强化学习学习使用 chain of thought，并报告性能同时随训练时计算和测试时计算提升。

## 关键贡献

- 把 test-time compute 明确作为 reasoning 能力扩展路径。
- 展示 reasoning-heavy benchmark 上 o1 相对 GPT-4o 的提升。
- 将 consensus sampling 和 learned scoring function 放入推理时计算谱系。
- 说明推理能力也可提升安全拒答边界等 robustness 任务。

## 对 AI 知识体系的归属

- 主归属：3. 推理与能力层
- 交叉链接：6. 评估与可靠性层
- 作用：提供现代 reasoning model 与 test-time compute 的官方案例。

## 关联

- [[concepts/TestTimeCompute]]
- [[Research: 推理时计算与 reasoning]]

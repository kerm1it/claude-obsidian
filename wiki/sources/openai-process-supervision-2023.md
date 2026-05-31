---
address: c-000234
type: source
title: "Improving mathematical reasoning with process supervision"
source_url: https://openai.com/index/improving-mathematical-reasoning-with-process-supervision/
source_type: research-blog
author: "OpenAI"
published: 2023-05-31
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - reasoning
  - process-supervision
  - evals
status: active
related:
  - "[[concepts/TestTimeCompute]]"
  - "[[concepts/ReasoningEvalVerifier边界]]"
---

# Improving mathematical reasoning with process supervision

**来源**：OpenAI Research
**URL**：https://openai.com/index/improving-mathematical-reasoning-with-process-supervision/

## 摘要

OpenAI 比较 outcome supervision 与 process supervision。文章说明逐步奖励正确推理步骤可以提升数学推理表现，并使推理过程更容易被人类审查。

## 关键贡献

- Process supervision 奖励每一步推理，而不是只奖励最终答案。
- 在 MATH 任务上，process-supervised reward model 比 outcome-supervised reward model 更可靠。
- 当生成多个候选解并用 reward model 选择时，process supervision 与 test-time search / rerank 自然连接。
- 文章明确指出跨数学领域的泛化仍需验证。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：3. 推理与能力层
- 作用：提供 verifier / reranker 如何约束 reasoning 的证据。

## 关联

- [[concepts/TestTimeCompute]]
- [[concepts/ReasoningEvalVerifier边界]]
- [[Research: 推理时计算与 reasoning]]
- [[Research: Reasoning eval verifier 边界]]

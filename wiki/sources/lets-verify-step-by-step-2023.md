---
address: c-000264
type: source
title: "Let's Verify Step by Step"
source_url: https://arxiv.org/abs/2305.20050
source_type: paper
author: "Hunter Lightman et al."
published: 2023-05-31
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - reasoning
  - process-supervision
  - prm
status: active
related:
  - "[[concepts/ReasoningEvalVerifier边界]]"
  - "[[concepts/TestTimeCompute]]"
sources:
  - "https://openai.com/index/improving-mathematical-reasoning-with-process-supervision/"
  - "https://github.com/openai/prm800k"
---

# Let's Verify Step by Step

**来源**：arXiv / OpenAI
**URL**：https://arxiv.org/abs/2305.20050

## 摘要

论文比较 outcome supervision 和 process supervision。Outcome supervision 只奖励最终结果，process supervision 对每个中间推理步骤给反馈；作者发布 PRM800K step-level human feedback 数据集。

## 关键贡献

- 将 reasoning verifier 明确拆成最终结果监督和过程监督。
- 在 MATH 任务上，process-supervised reward model 比 outcome-supervised reward model 表现更好。
- PRM800K 提供约 80 万 step-level 标签，成为 PRM 研究基准来源。
- Active learning 能降低过程标签成本，提高 process supervision 效率。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：2. 模型构建层、3. 推理与能力层
- 作用：说明 PRM 既是 reasoning eval，也是训练和 test-time search 的信号。

## 关联

- [[concepts/ReasoningEvalVerifier边界]]
- [[sources/openai-process-supervision-2023]]
- [[Research: Reasoning eval verifier 边界]]

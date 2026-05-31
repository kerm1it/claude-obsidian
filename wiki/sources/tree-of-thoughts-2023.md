---
address: c-000233
type: source
title: "Tree of Thoughts"
source_url: https://arxiv.org/abs/2305.10601
source_type: paper
author: "Shunyu Yao et al."
published: 2023-12-03
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - reasoning
  - planning
  - search
status: active
related:
  - "[[concepts/TestTimeCompute]]"
  - "[[concepts/AgentHarness与TraceEval]]"
---

# Tree of Thoughts

**来源**：arXiv:2305.10601
**URL**：https://arxiv.org/abs/2305.10601

## 摘要

Tree of Thoughts 把 Chain of Thought 扩展成搜索框架：模型生成多个“thought”作为中间状态，进行探索、self-evaluation、lookahead 和 backtracking。

## 关键贡献

- 解决单线 left-to-right reasoning 对规划和搜索任务的限制。
- 把模型推理看成搜索树，而不是单次文本生成。
- 适合初始选择影响全局结果的任务，例如规划、谜题和组合搜索。

## 对 AI 知识体系的归属

- 主归属：3. 推理与能力层
- 交叉链接：5. Agent 系统层
- 作用：把推理时计算从“多想”推进到“搜索与回溯”。

## 关联

- [[concepts/TestTimeCompute]]
- [[Research: 推理时计算与 reasoning]]

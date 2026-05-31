---
address: c-000216
type: source
title: "SIA: Self Improving AI with Harness & Weight Updates"
source_url: https://arxiv.org/abs/2605.27276
source_type: paper
author: "Prannay Hebbar et al."
published: 2026-05-26
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - self-improvement
  - harness
  - fine-tuning
status: active
related:
  - "[[concepts/Dream与SelfImprovement工程原语]]"
  - "[[concepts/AgentHarness与TraceEval]]"
---

# SIA: Self Improving AI with Harness & Weight Updates

**来源**：arXiv
**URL**：https://arxiv.org/abs/2605.27276

## 摘要

SIA 提出一个 self-improving loop：Feedback-Agent 同时更新 task-specific agent 的 harness 和 weights，并在法律分类、GPU kernel 优化、单细胞 RNA denoising 三个领域评估。

## 关键贡献

- 区分 harness-update 和 weight-update 两条路线，并尝试组合。
- Harness update 改工具、prompt、retry、search procedure；weight update 改领域直觉。
- 对本体系的价值是提醒：自我改进的回填目标可以分层，不是只有“改模型”一种。

## 对 AI 知识体系的归属

- 主归属：8. 自我改进与前沿层
- 交叉链接：5. Agent 系统层、2. 模型构建层、6. 评估与可靠性层
- 作用：提供 harness + weights 双回填的前沿研究样本。

## 关联

- [[concepts/Dream与SelfImprovement工程原语]]
- [[concepts/AgentHarness与TraceEval]]
- [[Research: Dream 与 self-improvement 工程原语]]

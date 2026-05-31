---
address: c-000278
type: source
title: "WorldSimBench: Towards Video Generation Models as World Simulators"
source_url: https://arxiv.org/abs/2410.18072
source_type: paper
author: "Yiran Qin et al."
published: 2024-10-23
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - world-models
  - simulation
  - embodied-agents
status: active
related:
  - "[[concepts/MultimodalEvalSimulationEval边界]]"
  - "[[concepts/AgentHarness与TraceEval]]"
---

# WorldSimBench

**来源**：arXiv
**URL**：https://arxiv.org/abs/2410.18072

## 摘要

WorldSimBench 评估视频生成模型作为 world simulator 的能力。它提出双重评估：显式感知评估和隐式操控评估，覆盖开放 embodied environment、autonomous driving 和 robot manipulation。

## 关键贡献

- 将世界模拟评估从视觉偏好推进到行动级评估。
- 显式评估用人类反馈训练 Human Preference Evaluator。
- 隐式评估检查生成视频是否能转化为正确控制信号。
- 说明 embodied world simulator 需要同时满足 visual fidelity 和 action-level consistency。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：3. 推理与能力层、5. Agent 系统层
- 作用：把 simulation eval 接到 embodied task 和控制信号。

## 关联

- [[concepts/MultimodalEvalSimulationEval边界]]
- [[Research: Multimodal eval simulation eval 边界]]

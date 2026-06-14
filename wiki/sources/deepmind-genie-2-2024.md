---
address: c-000241
type: source
title: "Genie 2: A large-scale foundation world model"
source_url: https://deepmind.google/blog/genie-2-a-large-scale-foundation-world-model/
source_type: research-blog
author: "Google DeepMind"
published: 2024-12-04
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - world-model
  - embodied-agents
  - simulation
status: active
related:
  - "[[concepts/多模态与世界模型边界]]"
  - "[[concepts/MultimodalEvalSimulationEval边界]]"
---

# Genie 2: A large-scale foundation world model

**来源**：Google DeepMind
**URL**：https://deepmind.google/blog/genie-2-a-large-scale-foundation-world-model/

## 摘要

Google DeepMind 将 Genie 2 定义为 foundation world model：从单张 prompt image 生成 action-controllable、playable 3D environments，可由人类或 AI agent 用键盘鼠标输入交互。

## 关键贡献

- 世界模型的关键不是“生成世界截图”，而是 action-conditioned simulation。
- Genie 2 可生成反事实轨迹，用于训练和评估 embodied agents。
- 模型展示长程记忆、对象交互、NPC、物理、光照、反射等 emergent capabilities。
- 研究仍处早期，生成能力和 agent 使用都需要继续改进。

## 对 AI 知识体系的归属

- 主归属：3. 推理与能力层
- 交叉链接：5. Agent 系统层、6. 评估与可靠性层
- 作用：把世界模型稳定定义为“可行动条件模拟”的系统，而不只是视频生成。

## 关联

- [[concepts/多模态与世界模型边界]]
- [[concepts/MultimodalEvalSimulationEval边界]]
- [[Research: 多模态与世界模型边界]]
- [[Research: Multimodal eval simulation eval 边界]]

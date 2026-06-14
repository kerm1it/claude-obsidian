---
address: c-000279
type: source
title: "SIMA: A generalist AI agent for 3D virtual environments"
source_url: https://deepmind.google/blog/sima-generalist-ai-agent-for-3d-virtual-environments/
source_type: research-blog
author: "Google DeepMind"
published: 2024-03-13
fetched: 2026-05-30
created: 2026-05-30
updated: 2026-06-12
tags:
  - ai
  - embodied-agents
  - simulation
  - evals
status: active
related:
  - "[[concepts/MultimodalEvalSimulationEval边界]]"
  - "[[concepts/多模态与世界模型边界]]"
sources:
  - "https://arxiv.org/abs/2404.10179"
---

# SIMA: A generalist AI agent for 3D virtual environments

**来源**：Google DeepMind
**URL**：https://deepmind.google/blog/sima-generalist-ai-agent-for-3d-virtual-environments/

## 摘要

SIMA 是 Google DeepMind 的 Scalable Instructable Multiworld Agent，用于在多个 3D 虚拟环境中根据自然语言指令行动。它只使用屏幕图像和语言指令，通过键盘鼠标输出控制角色。

## 关键贡献

- 使用 9 个商业视频游戏和 4 个研究环境训练/测试 generalist embodied agent。
- 评估 600 个基础技能，覆盖导航、物体交互和菜单使用。
- 展示跨游戏训练比单游戏专用 agent 更能泛化到未见环境。
- 说明虚拟世界是 embodied agent 评估和训练的 sandbox。

## 对 AI 知识体系的归属

- 主归属：5. Agent 系统层
- 交叉链接：6. 评估与可靠性层、3. 推理与能力层
- 作用：提供 embodied agent 在仿真/游戏环境中的 eval 模式。

## 关联

- [[concepts/MultimodalEvalSimulationEval边界]]
- [[Research: Multimodal eval simulation eval 边界]]

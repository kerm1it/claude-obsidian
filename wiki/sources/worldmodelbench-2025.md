---
address: c-000277
type: source
title: "WorldModelBench: Judging Video Generation Models As World Models"
source_url: https://arxiv.org/abs/2502.20694
source_type: paper
author: "Dacheng Li et al."
published: 2025-02-28
fetched: 2026-05-30
created: 2026-05-30
tags:
  - ai
  - world-models
  - video-generation
  - benchmark
status: active
related:
  - "[[concepts/MultimodalEvalSimulationEval边界]]"
  - "[[concepts/多模态与世界模型边界]]"
sources:
  - "https://worldmodelbench-team.github.io"
---

# WorldModelBench

**来源**：arXiv
**URL**：https://arxiv.org/abs/2502.20694

## 摘要

WorldModelBench 评估视频生成模型作为世界模型的能力。它指出已有视频 benchmark 过度关注视觉质量，忽略 physics adherence、instruction following 和 commonsense plausibility。

## 关键贡献

- 专门评估 video world modeling，而不是一般视频美观度。
- 检测物体尺寸异常、质量守恒违反等细微物理错误。
- 使用 67K 人类标签评估 14 个前沿模型，并训练自动 judger。
- 说明 world model eval 必须衡量物理一致性和常识，而不是只做人类偏好排序。

## 对 AI 知识体系的归属

- 主归属：6. 评估与可靠性层
- 交叉链接：3. 推理与能力层、5. Agent 系统层
- 作用：为“视频模型是否真是世界模型”提供评估边界。

## 关联

- [[concepts/MultimodalEvalSimulationEval边界]]
- [[concepts/多模态与世界模型边界]]
- [[Research: Multimodal eval simulation eval 边界]]

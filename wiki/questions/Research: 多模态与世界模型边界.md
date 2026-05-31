---
address: c-000237
type: synthesis
title: "Research: 多模态与世界模型边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - research
  - ai
  - multimodal
  - world-model
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/多模态与世界模型边界]]"
  - "[[concepts/Omni世界模型]]"
  - "[[concepts/TestTimeCompute]]"
  - "[[concepts/AgentHarness与TraceEval]]"
sources:
  - "[[sources/gemini-1-5-multimodal-long-context-2024]]"
  - "[[sources/openai-gpt-4o-2024]]"
  - "[[sources/openai-sora-world-simulators-2024]]"
  - "[[sources/deepmind-genie-2-2024]]"
  - "[[sources/world-models-2018]]"
  - "[[sources/rt-2-vla-2023]]"
  - "[[sources/gemini-coleads-origins-2026-05-30]]"
---

# Research: 多模态与世界模型边界

## Overview

多模态 / 世界模型稳定归入 [[domains/AI知识体系]] 第 3 层：它们描述模型运行时能处理和生成哪些模态，以及是否能模拟状态随时间和行动变化。它们会连接第 4 层上下文、第 5 层 agent/robot loop、第 6 层 eval 和第 7 层产品表面，但不需要新增顶层。

稳定区分：多模态是信号接口与融合能力，世界模型是动态预测与行动后果模型。

## Key Findings

- Gemini 1.5 显示多模态能力不只是“看图”，还包括在百万级上下文内对长文档、长视频和音频做检索与推理。（Source: [[sources/gemini-1-5-multimodal-long-context-2024]]）
- GPT-4o 把文本、视觉、音频端到端放进同一个模型，说明“原生多模态”与“多个模型串联 pipeline”在信息保真和延迟上不同。（Source: [[sources/openai-gpt-4o-2024]]）
- Sora 把视频生成描述为通向物理世界模拟器的路径，展示了 3D consistency、object permanence、world interaction 等 emergent simulation 能力，但也明确存在物理和状态变化限制。（Source: [[sources/openai-sora-world-simulators-2024]]）
- Genie 2 把世界模型推进到 action-controllable playable environments：agent 或人类采取 action，模型生成下一 observation，用于训练和评估 embodied agents。（Source: [[sources/deepmind-genie-2-2024]]）
- Ha & Schmidhuber 的 World Models 给出经典定义：学习环境的压缩时空表示，用它训练 agent，甚至让 agent 在模型“梦境”中学习。（Source: [[sources/world-models-2018]]）
- RT-2 说明多模态能力进入现实行动时，会变成 vision-language-action 模型：把机器人 observation、语言指令和动作放进同一训练格式。（Source: [[sources/rt-2-vla-2023]]）

## Stable Boundary

| 概念 | 主职责 | 归属 |
|---|---|---|
| Multimodal model | 多模态输入/输出、融合、转换 | 3. 推理与能力层 |
| World model | 状态、动态、行动后果、反事实预测 | 3. 推理与能力层 |
| Multimodal context | 把图像/音频/视频等组织成可用上下文 | 4. 上下文与知识层 |
| Embodied agent / VLA | 把 perception、language、action 放进 loop | 5. Agent 系统层 |
| Simulation eval | 评估一致性、物理、行动安全和泛化 | 6. 评估与可靠性层 |
| Voice/video/robot product | 把能力包装成用户可用体验 | 7. 产品与组织层 |

## 什么时候叫世界模型

仅仅能生成视频不足以稳定叫世界模型。至少需要满足其中多个条件：

- 能保持对象、角色、空间和时间一致性。
- 能预测 action 之后的下一 observation。
- 能生成反事实轨迹。
- 能用于 agent 训练、评估或规划。
- 能在未见环境或新对象上泛化。
- 能暴露可测试的物理、交互和安全边界。

## Open Questions

- 视频生成模型的“物理理解”如何和真实机器人控制对齐。
- 世界模型 eval 如何避免只评估视觉真实感，而忽略行动后果。
- 多模态 context、长上下文和 test-time compute 的预算如何统一管理。

## Filed Result

本轮归档为 [[concepts/多模态与世界模型边界]]，并更新 [[concepts/Omni世界模型]]。结论：多模态和世界模型是第 3 层能力，不新增顶层；进入产品时分别接第 4 层上下文、第 5 层行动系统、第 6 层 eval 和第 7 层体验约束。

---
address: c-000272
type: synthesis
title: "Research: Multimodal eval simulation eval 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - research
  - ai
  - multimodal
  - evals
  - simulation
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/MultimodalEvalSimulationEval边界]]"
  - "[[concepts/多模态与世界模型边界]]"
  - "[[concepts/AgentHarness与TraceEval]]"
sources:
  - "[[sources/mmmu-2023]]"
  - "[[sources/mathvista-2023]]"
  - "[[sources/video-mme-2024]]"
  - "[[sources/openai-gpt-4o-system-card-2024]]"
  - "[[sources/worldmodelbench-2025]]"
  - "[[sources/worldsimbench-2024]]"
  - "[[sources/deepmind-sima-2024]]"
  - "[[sources/embodiedbench-2025]]"
  - "[[sources/deepmind-genie-2-2024]]"
---

# Research: Multimodal eval simulation eval 边界

## Overview

Multimodal eval / simulation eval 主属 [[domains/AI知识体系]] 第 6 层：它把第 3 层多模态/世界模型能力、第 5 层 embodied agent 和第 7 层实时产品风险连接起来。稳定边界是：多模态 eval 测跨信号理解、生成和推理；simulation eval 测时间、物理、行动后果和闭环环境状态。

## Key Findings

- MMMU 将多模态理解推进到大学级跨学科题：图表、地图、表格、化学结构等需要专家知识与视觉推理，不只是看图问答。（Source: [[sources/mmmu-2023]]）
- MathVista 说明视觉数学推理需要同时评估感知、图形理解、数学推导和自我验证，单纯文字数学 benchmark 不够。（Source: [[sources/mathvista-2023]]）
- Video-MME 把视频 eval 拆成短/中/长视频、多视觉领域、音频和字幕融合，说明多模态 eval 必须覆盖时间维度和多信号输入。（Source: [[sources/video-mme-2024]]）
- GPT-4o system card 显示原生音频/视觉/文本模型发布时，eval 必须覆盖 unauthorized voice generation、speaker identification、sensitive inference、disallowed audio content 和 Preparedness 风险。（Source: [[sources/openai-gpt-4o-system-card-2024]]）
- WorldModelBench 指出现有视频生成评估过度关注视觉质量，忽略 physics adherence、instruction following 和 commonsense plausibility；因此需要专门 world-model eval。（Source: [[sources/worldmodelbench-2025]]）
- WorldSimBench 把世界模拟评估拆成显式视觉偏好和隐式行动评估：不仅看视频像不像，还看生成状态能否转化为正确控制信号。（Source: [[sources/worldsimbench-2024]]）
- Genie 2 将世界模型用于生成可交互 3D 环境，可用于训练和评估 embodied agents；这把 simulation eval 接到 agent 自我改进和环境泛化。（Source: [[sources/deepmind-genie-2-2024]]）
- SIMA 和 EmbodiedBench 显示 embodied eval 的核心不是回答，而是在虚拟 3D 世界中根据语言目标采取动作，并评估导航、物体交互、空间感知、长期规划和泛化。（Source: [[sources/deepmind-sima-2024]]、[[sources/embodiedbench-2025]]）

## Classification

| 评估类型 | 主归属 | 输入 | 输出 |
|---|---|---|---|
| Static multimodal eval | 6. 评估与可靠性层 | 图像/图表/文档 + 问题 | accuracy、错误类型、domain split |
| Video/audio eval | 6. 评估与可靠性层 | 视频、音频、字幕、长上下文 | temporal reasoning、event QA、融合质量 |
| Generation safety eval | 6. 评估与可靠性层 | 图像/音频/视频输出 | safety label、moderation、release gate |
| World-model eval | 6. 评估与可靠性层 | 生成视频或未来状态 | physics、object permanence、controllability |
| Simulation / embodied eval | 6. 评估与可靠性层 | 环境、动作、agent trace | task success、unsafe action、generalization |

## Stable Pattern

`capability claim → eval matrix → benchmark + private tasks → human/judge calibration → simulator state checks → product or training gate`

第 6 层的关键不是追一个总分，而是把能力拆成矩阵：模态、时间、任务、风险、环境和产品 SLO。只要模型进入行动或生成世界，最终状态和物理/安全违反比视觉偏好更重要。

## Contradictions

- 视频生成模型可以产生逼真画面，但 WorldModelBench 和 WorldSimBench 都指出视觉质量不足以证明世界模型能力。结论：world model claim 必须通过物理、一致性、行动条件和环境状态评估。
- 仿真环境能低成本生成任务，但 sim-to-real gap 会让虚拟成功率高估真实可靠性。结论：simulation eval 是必要中间层，不是最终产品安全证明。

## Open Questions

- 如何给多模态 agent 设计统一 trace schema，使视觉、音频、动作和环境状态都能被回放。
- 自动 VLM judge 如何校准到物理 ground truth，而不是只对齐人类视觉偏好。
- 世界模型生成的合成环境如何防止污染训练、eval 和 self-improvement 反馈环。

## Filed Result

本轮归档为 [[concepts/MultimodalEvalSimulationEval边界]]，并回填 [[domains/AI知识体系]]。结论：multimodal eval / simulation eval 主属第 6 层，是第 3 层多模态与世界模型、第 5 层 embodied agent、第 7 层实时产品和第 8 层自我改进之间的质量门。

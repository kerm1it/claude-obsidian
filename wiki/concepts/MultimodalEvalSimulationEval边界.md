---
address: c-000271
type: concept
title: "Multimodal Eval / Simulation Eval 边界"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - multimodal
  - evals
  - simulation
  - world-models
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[concepts/多模态与世界模型边界]]"
  - "[[concepts/ReasoningEvalVerifier边界]]"
  - "[[concepts/AgentHarness与TraceEval]]"
  - "[[concepts/Omni世界模型]]"
sources:
  - "[[Research: Multimodal eval simulation eval 边界]]"
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

# Multimodal Eval / Simulation Eval 边界

Multimodal eval / simulation eval 是第 6 层评估与可靠性机制：它评估模型是否真的能跨模态理解、生成、推理、保持时序一致性、模拟物理世界，并在 agent 或机器人场景中安全完成任务。

主归属：**6. 评估与可靠性层**。

一句话：**multimodal eval 判断“模型是否正确处理多种信号”，simulation eval 判断“模型生成或预测的世界是否能经得起时间、物理和行动检验”。**

## 类型边界

| 类型 | 评估对象 | 典型指标 | 稳定职责 |
|---|---|---|---|
| 静态多模态理解 | 图像、图表、表格、地图、公式、文档 | accuracy、OCR、grounding、domain reasoning | 评估跨视觉与语言的理解 |
| 视觉数学/科学推理 | 图形、几何、科学图表、视觉题 | answer accuracy、reasoning error、self-verification | 评估视觉感知 + 抽象推理 |
| 视频/音频/字幕理解 | 长短视频、音频、字幕、多源输入 | temporal reasoning、event QA、long-context recall | 评估时序和跨信号融合 |
| 多模态生成安全 | 图像、语音、视频、音乐输出 | safety、voice misuse、copyright、sensitive inference | 评估产品发布风险 |
| 世界模型 eval | 生成视频、未来 observation、action-conditioned rollout | object permanence、physics adherence、controllability、counterfactual | 评估动态模拟能力 |
| Simulation / embodied eval | agent 在仿真或真实环境中的行动 | task success、collision、unsafe action、generalization、sim-to-real | 评估行动后果和闭环控制 |

## 与相邻概念的区别

| 概念 | 边界 |
|---|---|
| [[concepts/多模态与世界模型边界]] | 定义第 3 层能力；本页定义第 6 层如何评估这些能力 |
| [[concepts/ReasoningEvalVerifier边界]] | reasoning verifier 评估推理过程；multimodal eval 还要评估感知、时序、物理和行动 |
| Trace eval | 评估 agent 轨迹；embodied eval 是 trace eval 在视觉/空间/动作环境中的特殊形态 |
| Serving eval | 评估延迟、吞吐和成本；多模态产品还要测实时音视频延迟和模态安全 |
| Benchmark | benchmark 是任务集；simulation eval 更关注环境状态变化和可重复 closed-loop 测试 |

## 稳定链路

`modality inputs / generated media / action rollout → task-specific grader + human/judge + simulator state checks → score / violation / failure reason → product gate / training data / harness fix / world-model improvement`

## 工程实践

1. 先画 eval matrix：输入模态、输出模态、任务类型、时序长度、风险面和用户场景。
2. 静态多模态理解用 MMMU、MathVista 等任务集测知识、视觉和推理组合。
3. 视频和音频任务必须测 temporal reasoning、字幕/音频融合、长视频召回和事件定位。
4. 生成模型不能只做人类偏好；必须加 instruction following、artifact、物理一致性、安全和版权检查。
5. 世界模型必须测 object permanence、physics adherence、counterfactual、action-conditioned prediction 和 controllability。
6. Embodied agent 必须在环境中闭环评估：最终状态、路径、碰撞、低层动作、恢复和跨环境泛化。
7. 自动 judge 必须用人工样本校准；视觉质量偏好不能替代行动正确性。

## 评估方式

- 多模态理解：accuracy、domain split、image-type split、OCR/diagram/table failure analysis。
- 视觉推理：感知错误、数学错误、步骤错误、自我验证失败。
- 视频理解：短/中/长视频分层、temporal order、event localization、audio/subtitle ablation。
- 生成质量：prompt adherence、visual fidelity、temporal consistency、artifact rate、safety violation。
- 世界模型：physics adherence、object permanence、mass/scale consistency、action-conditioned future prediction。
- Embodied agent：task success、unsafe action、collision、low-level manipulation、planning horizon、sim-to-real gap。
- 产品：P95/P99 realtime latency、privacy, consent, moderation, voice/persona misuse, fallback/human takeover。

## 过时风险

- 多模态 benchmark 会快速饱和；必须保留私有真实任务和分布外测试。
- VLM judge 会继承视觉盲点和偏好偏差，不能替代人工和 simulator ground truth。
- 视频生成越逼真，越容易误把视觉真实感当作物理理解。
- 仿真环境可控但可能和真实世界脱节；sim-to-real 是独立风险。
- 产品化多模态新增隐私、人格化语音、版权、敏感属性推断和实时安全风险。

## 稳定结论

Multimodal eval / simulation eval 不新增顶层。它是第 6 层对第 3 层多模态/世界模型能力、第 5 层 embodied agent 行动和第 7 层实时产品体验的质量门。

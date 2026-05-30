---
type: entity
name: Gemini
kind: ai-model-family
org: "[[entities/GoogleDeepMind|Google DeepMind]]"
address: c-000163
created: 2026-05-30
tags:
  - google
  - deepmind
  - llm
  - multimodal
status: active
related:
  - "[[concepts/单模型统一策略]]"
  - "[[concepts/蒸馏传承]]"
  - "[[concepts/Omni世界模型]]"
  - "[[concepts/模型即产品]]"
  - "[[entities/GoogleDeepMind]]"
---

# Gemini

Google DeepMind 的多模态大语言模型家族。得名于 Google Brain 和 DeepMind 两个团队合二为一（双子座）。

## 起源

2023 年 Jeff Dean 写了一份半页备忘录，主张停止 Brain 和 DeepMind 各自独立开发 LLM 的碎片化状态，合并所有算力和人才构建一个统一的强大模型。Gemini 项目由此诞生。

三个前置理念来自 Pathways 项目：
- **多模态**：单一模型处理所有模态
- **稀疏激活**：不同任务激活模型不同部分
- **统一模型**：一个模型做所有事

## 模型代际

- **Gemini 1.0**：初代，确立基础
- **Gemini 1.5 / 2.0 / 2.5**：多代迭代，每代 Flash 开始超越上代 Pro
- **Gemini 3.5 Flash**（2026-05）：最新 Flash 版本，聚焦编码和 agentic 体验
- **Gemini Omni**：多模态生成模型，理解并生成文本/图像/音频/视频，定位为"世界模型"

## 核心哲学

- **"一个盒子"**：Google 早期搜索愿景——一个搜索框做所有事——如今通过 Gemini 在 AI 层面实现
- **用户驱动改进**：通过大量用户使用反馈改进模型，区别于纯基准驱动的闭门造车
- **蒸馏传承**：每代 Flash 模型继承上代 Pro 的智能，技术本质与 Hinton 原始蒸馏论文一致

## 团队分工（2026-05）

- Jeff Dean：推理硬件
- Koray Kavukcuoglu：模型方向 + 产品对齐
- Noam Shazeer：模型研发
- Oriol Vinyals：Agent 深度发展
- Logan Kilpatrick：开发者关系

## 2027 预测

Koray 预测 IO 2027 将展示模型自我学习——模型和 agent 用于改进 Gemini 自身。

## 来源

- [[sources/gemini-coleads-origins-2026-05-30|Gemini 联合负责人谈项目起源与未来]]（2026-05-29）

---
type: source
title: "Gemini 联合负责人谈项目起源与未来"
source_url: https://youtu.be/8hfpLa5wPGo
source_kind: youtube
channel: Google for Developers
fetched: 2026-05-30
published: 2026-05-29
duration: 42min
speakers:
  - Logan Kilpatrick
  - Jeff Dean
  - Koray Kavukcuoglu
  - Noam Shazeer
  - Oriol Vinyals
address: c-000157
created: 2026-05-30
updated: 2026-06-12
tags:
  - google
  - gemini
  - ai-model
  - distillation
  - interview
status: ingested
related:
  - "[[entities/Gemini]]"
  - "[[concepts/蒸馏传承]]"
  - "[[concepts/单模型统一策略]]"
  - "[[concepts/模型即产品]]"
  - "[[concepts/自我改进AI循环]]"
---

# Gemini 联合负责人谈项目起源与未来

Google for Developers 在 Gemini 3.5 Flash 发布之际，由 Logan Kilpatrick 主持，与四位核心构建者——Jeff Dean、Koray Kavukcuoglu、Noam Shazeer、Oriol Vinyals——在 Gradient Canopy 对谈，追溯 Gemini 项目起源、单模型统一策略、Flash 蒸馏传承，以及 IO 2027 预测。

## 关键论点

### 1. Gemini 起源：一张半页备忘录

Jeff Dean 写了一份半页备忘录，认为 Google Brain 和 DeepMind 各自独立开发 LLM 是"愚蠢的"——分裂了思想和算力。Gemini（双子座）得名于两个团队合二为一。他向 Koray 出售了 Google 工作 offer（2000 年），又招募了 Oriol（2012 年）；收购 DeepMind 时，Jeff 和 Koray 在伦敦做了一场即兴"代码审查"，看了 13 个 30 分钟演讲后用"看代码"做最终判断。 → [[concepts/单模型统一策略]]

### 2. Flash 超越 Pro：蒸馏传承

每代 Flash 模型都打包了上一代 Pro 的智能——这一模式甚至在加速。Koray 确认蒸馏技术本质上与 Hinton 原始论文相同："一个非常好的老师 + 一个学生，用一些 modest tweaks……精神一样。"Noam 比喻："像挤柠檬汁——好部分挤出来，放进小模型杯子里。" → [[concepts/蒸馏传承]]

### 3. 模型即产品

"模型就是产品"——Logan 的核心信条。Jeff 补充：用户使用量直接反馈模型改进方向，与 Google 搜索多年积累的改进逻辑一致。Oriol 强调"你不能在黑盒中构建智能"——前沿研究和技术前沿必须与用户前沿同时推进。 → [[concepts/模型即产品]]

### 4. "一个盒子"哲学的实现

Jeff 回忆 Google 早期"一个搜索框做所有事"的愿景——背后却是各自独立的后端。现在 Gemini 真正实现了"一个后端支持一个前端"："我们终于为前端建好了后端，而且我们有正确的接口，因为我们建了一个盒子。"

### 5. Omni 与世界模型

Gemini Omni 将多模态理解（文本/图像/音频/视频）与生成统一训练，Koray 称其为从"理解+文本输出"到"真正世界模型"的转变——模型需理解物理动态、模拟前滚，并基于未来模拟做决策。Jeff 补充：多模态不仅是人类感官模态，还应涵盖基因组序列、化学结构、机器人抓取数据、激光雷达等科学数据。→ [[concepts/Omni世界模型]]

### 6. 持续学习的挑战

Jeff 表示失望之一是持续学习（continual learning）和更有机的模型架构进展不如预期。但 Koray 认为模型仍有"大量未开发容量"——当今模型规模与 3-4 年前相当，却不断装入更多能力。

### 7. 评估的困难

Oriol 指出评估是"出奇地难"——从论文中的数字表格到用户反馈驱动，如何在"不泄露到数据集"的前提下准确评估下一波能力，仍是未解难题。

### 8. 2027 预测：自我学习

Koray 预测 IO 2027 将讨论**模型自我学习（self-learning）**——模型和 agent 将用于改进 Gemini 自身。"我们将能指出模型中某个非常重要的部分是由模型和 agent 生成的。"Noam 补充：工具延迟将成为 agent 瓶颈——"30 天中的 29.5 天都在等待。"

## 演讲者

- [[Jeff Dean]] — Google 首席科学家，Gemini 联合创始人
- [[Koray Kavukcuoglu]] — Google DeepMind CTO
- [[Noam Shazeer]] — Google DeepMind，Gemini 联合负责人
- [[Oriol Vinyals]] — Google DeepMind，Gemini 联合负责人
- [[Logan Kilpatrick]] — Google DeepMind，主持人

## 关联

- [[concepts/单模型统一策略]] — Google Brain + DeepMind 合并背后的决策逻辑
- [[concepts/蒸馏传承]] — Flash 打包 Pro 智能的模式与本质
- [[concepts/模型即产品]] — 用户使用驱动模型改进（Alex Albert 也独立主张）
- [[concepts/自我改进AI循环]] — Koray 的 2027 自我学习预测与此方向一致
- [[concepts/Omni世界模型]] — 从多模态理解到物理世界模拟

## 提取说明

YouTube 自动英文字幕（yt-dlp），44,465 字符。AI 转录有少量错字（如 "Oral" 应为 "Oriol"、"Demind" 应为 "DeepMind"、"Gnome" 应为 "Noam"），摘要中已纠正。

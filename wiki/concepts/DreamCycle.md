---
type: concept
address: c-000034
title: "Dream Cycle（梦境循环）"
created: 2026-05-11
updated: 2026-05-11
tags:
  - agent-memory
  - maintenance
  - automation
status: active
related:
  - "[[entities/GBrain]]"
  - "[[concepts/CompiledTruth时间线模式]]"
  - "[[concepts/Dream与SelfImprovement工程原语]]"
  - "[[sources/gbrain-2026-05-11]]"
---

# Dream Cycle（梦境循环）

**来源**：[[entities/GBrain]] by [[people/GarryTan]]
**类型**：自动化夜间维护机制

---

## 是什么

Dream Cycle 是 GBrain 的夜间自动维护流程，类比人类睡眠时大脑的记忆巩固过程。在低负载时段自动运行，对知识库做"深度整理"。

## 包含任务

1. **综合（Synthesis）** — 将时间线事件蒸馏回 [[concepts/CompiledTruth时间线模式|Compiled Truth 区]]
2. **模式检测（Pattern Detection）** — 识别跨页面的重复主题、关系集群
3. **反向链接强制执行（Backlink Enforcement）** — 确保所有实体页面的双向链接完整
4. **引用修复（Citation Fixing）** — 清理断链、更新过期引用

## 类比

人类睡眠时的**记忆巩固**：短期记忆（时间线事件）→ 长期记忆（编译事实）。Dream Cycle 做的是 AI 版本的同样事情。

## 在 GBrain 中的位置

Dream Cycle 通过 [[concepts/Minions任务队列|Minions 任务队列]] 的 cron 任务触发，是 GBrain 21 个自主 cron 任务之一。

## Anthropic 官方同构实现

2026-05-11，Anthropic 发布 [[concepts/AnthropicDreaming]]，功能与 Dream Cycle 高度同构：
- 同样是离线批处理、模式提取、记忆整理
- 区别在于 Anthropic Dreaming 以**多 Agent session transcript** 为输入，输出 memory store diff
- GBrain Dream Cycle 以**时间线事件**为输入，输出 Compiled Truth 更新

两者均证明"异步记忆维护"是 Agent 系统的关键过程层原语。

## 关联概念

- [[concepts/CompiledTruth时间线模式]] — 蒸馏的目标结构
- [[concepts/Dream与SelfImprovement工程原语]] — 将 Dream 放回第 8 层反馈环
- [[concepts/Minions任务队列]] — 执行载体
- [[entities/GBrain]] — 实现系统
- [[concepts/AnthropicDreaming]] — Anthropic 官方同构实现（2026-05-11 发布）

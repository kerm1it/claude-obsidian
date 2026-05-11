---
address: c-000063
type: concept
title: "Native Resolution Computer Use（原生分辨率电脑操控）"
created: 2026-05-12
updated: 2026-05-12
tags:
  - anthropic
  - claude
  - computer-use
  - opus-4-7
  - agent
status: active
related:
  - "[[concepts/ExpandingToolkit]]"
  - "[[domains/Claude-Code]]"
  - "[[people/Lucas]]"
---

# Native Resolution Computer Use（原生分辨率电脑操控）

**来源：** [[people/Lucas]]（Anthropic Research PM），Code with Claude 2026  
**模型：** Claude Opus 4.7  
**参见：** [[sources/the-expanding-toolkit-2026-05-12]]

---

## 是什么

Opus 4.7 支持**原生分辨率截图输入**，返回 1:1 像素坐标，无需开发者手写缩放代码。

---

## 解决了什么问题

**旧范式（Before）**：
1. 截 1080p 截图
2. 缩小到 Claude 的像素限制
3. 记录缩放因子
4. 模型输出点击坐标
5. 将坐标放大回原始分辨率
6. 包一层重试 + 验证逻辑

→ "一堆图像胶水代码"

**新范式（After）**：
- 直接发送原始截图（支持到 1440p）
- Claude 返回 1:1 像素坐标
- **缩放数学完全消失**

---

## 评测表现：OSWorld

| 时间 | Claude 得分 |
|---|---|
| 不到 12 个月前 | < 50% |
| 2026-05-06（Opus 4.7） | **78%**（目标 80%）|

OSWorld 评测 Claude 完成专业软件和消费级软件中复杂任务的能力。78% → 被认为正处于"宽泛可用性临界点"。

---

## 实践建议

- **4K 及以上**：仍建议在发送前自行降采样
- **≤ 1440p**：建议实验不同分辨率和图像格式
  - JPEG / PNG / WEBP 压缩方式不同，产生不同压缩失真
  - 针对具体 UI 测试，找到最佳组合

---

## Claude Code：Claude in Chrome

**扩展：** `claude.ai/chrome`

Claude Code 可以直接操控用户的真实 Chrome 浏览器会话，包括本地开发页面。

**Demo 展示的工作流（agentic bug fix loop）**：
1. Claude Code 打开 Chrome，加载项目看板
2. 自行复现 Bug（新建 Card 不工作、Drag & Drop 落错列）
3. 切回代码编辑，写 Fix
4. 切回浏览器，验证修复
5. 汇报所有变更

意义：软件是给人类用的，必须用人类的方式测试。Computer Use 让 Claude 在开发周期中**自主闭环测试**，无需开发者手把手指引。

---

## 与 ExpandingToolkit 的关系

原本需要开发者维护的缩放/坐标胶水代码，现在由 Opus 4.7 内置吸收——是 [[concepts/ExpandingToolkit]] 在 computer use 维度的直接体现。

---

## 来源

- [[sources/the-expanding-toolkit-2026-05-12]]

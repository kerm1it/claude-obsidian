---
type: source
address: c-000146
title: "How to Build a Self-Improving Company with AI"
created: 2026-05-22
updated: 2026-05-22
tags:
  - yc
  - ai-native
  - self-improving
  - closed-loop
  - org-design
  - youtube
status: active
related:
  - "[[entities/YCombinator]]"
  - "[[concepts/自我改进AI循环]]"
  - "[[concepts/软件即临时物]]"
  - "[[concepts/公司大脑]]"
  - "[[concepts/封闭循环公司]]"
  - "[[concepts/Token最大化]]"
  - "[[sources/yc-diana-ai-company-ground-up-2026-05-22]]"
---

# How to Build a Self-Improving Company with AI

**来源**：YouTube — YC Root Access 频道  
**链接**：https://www.youtube.com/watch?v=t-G67yKAHBQ  
**发布**：2026 年（YC Root Access）  
**演讲者**：YC 合伙人（未具名，引用 Diana 的先前演讲）  
**关联**：基于 [[sources/yc-diana-ai-company-ground-up-2026-05-22]] + Jack Dorsey 推文

---

## 摘要

YC 合伙人在同一活动中的配套演讲，将 Diana 的框架延伸为"公司即递归自我改进 AI 循环"。提出五层 AI 循环架构，分享 YC 内部实际运行的自我改进案例（用户手册再生、智能体隔夜修复查询），并深化"软件即临时物 / 公司大脑"的架构哲学。

---

## 关键要点

### 罗马军团比喻

> "Most companies today are organized like a Roman legion where human beings are the conduit for information flowing up and down."

Jack Dorsey 的洞见：层级组织是假设"人是信息导管"的产物。AI 打破了这个假设。

### [[concepts/自我改进AI循环]]

公司 = 递归自我改进 AI 循环的集合。五层架构：

| 层 | 作用 | 示例 |
|----|------|------|
| **Sensor（感知层）** | 采集外部信息 | 客户邮件、支持票、代码变更、取消订阅、产品遥测 |
| **Policy（策略层）** | 决策规则 | 什么可以自主做、什么必须请示人类、什么必须记录 |
| **Tool（工具层）** | 确定性 API | 查数据库、查日历（Gary 的 skills/code）|
| **Quality Gate（质量门）** | 验证 | 评估检查、安全过滤、高风险人工审核 |
| **Learning Mechanism（学习机制）** | 闭环反馈 | 系统与真实世界交互 → 发现失败 → 循环回感知层 |

关键：每一步都尽量减少人工干预 → 系统在你睡觉时越来越好

### YC 内部实案

**阶段 1**（工具 Agent）：查询 YC 数据库 → 上次 office hours 是什么时候？
**阶段 2**（RAG Agent）：结合上下文推荐 5 位相关 founder 介绍
**阶段 3（顿悟）**：监控 Agent 观察所有 YC 员工的查询 → 发现哪些成功/失败 → 分析原因 → **隔夜自动写代码、提 merge request、agent review → 合并 → 部署** → 第二天同样查询成功

> "That's not just AI making you 20-30% more valuable. It is the AI going through this loop to figure out how to self-improve."

### 更多自我改进示例

- **产品分析循环**：Agent 分析销售漏斗摩擦 → 研究最佳实践 → 设计 A/B 测试 → 运行一周 → 选最优 → 部署 → 循环
- **客服建议循环**：客户建议流入 → CPO/CTO 型 Agent 判断采纳/丢弃 → 采纳则隔夜写代码 → 部署 → 客户收到改进，全程无人参与

### Token 经济学（YC 数据）

> "We are seeing companies get to demo day with about 5x more revenue per employee than they did 18 months ago."

- Demo Day 收入/人效已提升 5x，预计延续到 A 轮 B 轮
- 约束从人头数 → Token 用量
- 现阶段衡量方式：追踪谁在 token maxing，谁没有（方向性正确，极端情况会被博弈）

### 中层管理已死

> "I think middle management is done. AI should be doing the coordination."

只保留两个角色（对比 Diana 的三种，删去 AI Founder 型）：
- **IC**：构建者 + 运营者
- **DRRI**：单人直接负责可测量结果

### [[concepts/公司大脑]]

公司大脑 = 所有数据 + 邮件 + DM + skills + knowhow 的中心
人类 = 围绕在边缘，与现实世界接触

人类保留的场景：
- 高风险、高情绪时刻（联创关系破裂等）
- 新颖情境、伦理判断
- 未来 20 年：面对面销售对话

### [[concepts/软件即临时物]]

> "The valuable part is the comprehension inside people's heads. The software on top of it is ephemeral."

- 数据和业务上下文：永久保存（Gary：所有邮件存 Markdown）
- 软件/仪表盘：**一次性**，随时用 AI 重新生成
- 模型两个月后更强？扔掉旧软件，用原始指令集重新生成

### YC 用户手册再生案例

Haj（YC 合伙人）：
- 3 个月积累 2,000 小时 office hours 录音
- 提炼分类（融资/招聘/联创争议等）→ 重新生成 YC 用户手册
- 一个周末产出 **150 页**，质量显著优于原版（写于 5-10 年前）
- 每月自动更新：新建议与现有用户手册对比 → 采纳或丢弃
- 结论：用户手册成为**持续进化的活体大脑**

### 可记录即存在

> "If it is recorded, it happened to the AI. If it did not get recorded, it did not happen to your intelligence."

所有对话、邮件、DM、会议 → 必须记录；否则对 AI 不存在

---

## 关联概念（新建）

- [[concepts/自我改进AI循环]] — 五层架构；递归自我改进；隔夜自动修复
- [[concepts/软件即临时物]] — 数据/上下文永久，软件一次性可重生
- [[concepts/公司大脑]] — 数据+skills 是大脑；人类在边缘

## 关联概念（深化）

- [[concepts/封闭循环公司]] — 本演讲是对 Diana 框架的技术化深化
- [[concepts/可查询组织]] — "可记录即存在" = 可查询的极致表述
- [[concepts/Token最大化]] — 增加 YC 实证数据（Demo Day 5x revenue/employee）
- [[concepts/DreamCycle]] / [[concepts/AnthropicDreaming]] — YC 案例是同一模式的又一独立实现
- [[concepts/代码仓库即记录系统]] — 软件即临时物 × 仓库即记忆

---

## Extraction Notes

- YouTube URL 直接被 NotebookLM 接受
- 14,669 字符；YC Root Access 频道；演讲者未在转录中具名
- 演讲者明确引用 Diana 演讲和 Jack Dorsey 推文；Gary、Pete、Haj 为同场其他 YC 合伙人

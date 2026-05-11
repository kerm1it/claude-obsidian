---
address: c-000038
type: source
title: "Running an AI-native engineering org — Fiona Fung（Code with Claude 2026）"
created: 2026-05-11
updated: 2026-05-11
tags:
  - youtube
  - engineering-org
  - ai-native
  - anthropic
  - claude-code
  - management
status: active
related:
  - "[[people/FionaFung]]"
  - "[[entities/CodeWithClaude]]"
  - "[[entities/Anthropic]]"
  - "[[concepts/AI原生工程组织]]"
  - "[[concepts/JIT规划]]"
  - "[[concepts/瓶颈转移论]]"
  - "[[domains/Claude-Code]]"
source_url: "https://www.youtube.com/watch?v=igO8iyca2_g"
raw_file: ".raw/articles/ai-native-engineering-org-2026-05-11.md"
---

# Running an AI-native engineering org — Fiona Fung

**来源：** YouTube，[[entities/CodeWithClaude]] 大会（2026-05-06，旧金山）  
**演讲者：** [[people/FionaFung]]（Anthropic Claude Code & Cowie 工程与产品负责人）  
**时长：** 约 30 分钟  
**链接：** https://www.youtube.com/watch?v=igO8iyca2_g

---

## 核心主题

Fiona Fung 分享了她在 Anthropic 领导 Claude Code 工程团队的实践，以及当 AI 成为工程基础设施后，团队需要主动重写的五类规范。

---

## 五大主题

### 1. 瓶颈已转移（The Shift）

> "What served you prior may not serve you any longer."

- **旧瓶颈**：编码吞吐量 → 所有流程（Waterfall/Agile/设计文档/Code Review SLA）都围绕"编码很贵"而设计
- **新瓶颈**：验证、Code Review、跨职能合作（法务/安全）、可维护性
- 类比：从 CD-ROM 时代（硬截止日期）→ 在线分发，每次分发方式改变都迫使流程更新

参见：[[concepts/瓶颈转移论]]

### 2. 需要重写的团队规范

| 规范 | 变化 |
|------|------|
| 规划 | 减少长期规划，改为 [[concepts/JIT规划]] |
| 技术争论 | 代码赢：直接生成多个 PR 对比，不去白板 |
| 设计文档 | 大幅减少；讨论移入 PR 或原型 |
| 代码审查 | Claude 负责 style/lint/bug；人类保留法务/安全/产品品位 |
| 代码归属 | 不问"谁写的"，问"你真正想问的是什么"（下钻法） |
| Onboarding | 上手时间大幅缩短 |

### 3. 团队构成

Fiona 在 Claude Code 团队上索引两类工程师：
- **创造性构建者 + 产品感**：好奇心强、能快速迭代到令人愉悦的体验
- **深度系统专家**：分布式系统等硬核能力（Claude Code Remote 就需要这类人）

**不再看重**：原始编码吞吐量  
**组织形态**：尽量扁平；管理者先以 IC 身份入职（重狗粮）

### 4. 推行方式

Claude Code 团队的核心原则（每隔几个月审视一次是否仍有效）：
1. **每位成员都用 Claude Code**（含跨职能伙伴）
2. **Claude 化一切能 Claude 化的事**（验证、自动化、日常工作流）
3. **明确许可干掉旧流程**（鼓励团队主动识别并删除无效流程）

各 pod 保留高度自主权（triage、规划、on-call、优先 Claudify 哪些工作流）。

### 5. 效果信号

Fiona 无法公开具体数字，但分享三个指标方向：
- **Onboarding 上手时间**：大幅缩短 ↓
- **PR 周期时间**：缩短 ↓（同时也能暴露 CI/基础设施瓶颈）
- **Claude 辅助提交率**：几乎 100%；4 个月内未见无辅助提交

### 6. 开放问题

- iOS/Android 双轨团队在角色模糊化后是否仍合理？
- 全自动化审查的边界在哪里？（trust but verify 的平衡点）
- 模型能力持续提升 → 边界会随模型更新而变化

---

## 关键引语

> "In technical debates, code wins." — 直接生成多个 PR 代替白板讨论

> "Explicitly permission to kill old processes." — 流程不会自我消亡，需要授权

> "What's better than me finding a bug? Shift left." — 更多自动化，更早捕获

> "Pick your noisiest workflow." — 从最让团队头痛的流程开刀

---

## 关联

- [[concepts/AI原生工程组织]] — 整体框架
- [[concepts/JIT规划]] — 即时规划模式
- [[concepts/瓶颈转移论]] — 核心论点
- [[concepts/AmdahlsLawInAI]] — 与 Dario 对谈中提到的同类观点
- [[domains/Claude-Code]]
- [[entities/CodeWithClaude]]
- [[people/FionaFung]]

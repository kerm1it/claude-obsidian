---
address: c-000040
type: concept
title: "AI 原生工程组织"
created: 2026-05-11
updated: 2026-05-11
tags:
  - engineering-org
  - ai-native
  - management
  - claude-code
status: active
related:
  - "[[concepts/瓶颈转移论]]"
  - "[[concepts/JIT规划]]"
  - "[[concepts/AmdahlsLawInAI]]"
  - "[[people/FionaFung]]"
  - "[[domains/Claude-Code]]"
---

# AI 原生工程组织

当 AI 成为工程基础设施后，团队的组织形态、规范和文化必须主动重写。不是在旧流程上叠加 AI，而是从底层重新设计。

---

## 核心原则

来自 [[people/FionaFung]] 在 [[entities/CodeWithClaude]] 的实践：

### 1. 承认瓶颈已转移

参见 [[concepts/瓶颈转移论]]。原有流程是为了对抗"编码吞吐量昂贵"而设计的，现在这个假设已失效。

### 2. 团队规范重写清单

**减少：**
- 六个月路线图 → 改为 [[concepts/JIT规划]]
- 编码前必写设计文档 → 多数情况改为 PR 或原型
- 白板技术辩论 → 直接生成多个 PR 对比（"代码赢"）
- 按输出量衡量工程师价值

**保持/加强：**
- 验证与自动化（"验证左移"：更多 CI/CD，更早捕获 bug）
- 法务/安全领域的人工审查
- 产品感与设计品位（Claude 在此尚有局限）
- 代码库作为单一事实来源

**新增：**
- 全员（含跨职能伙伴）使用 AI 工具
- 明确许可干掉不再有效的旧流程（每隔几个月审视）
- 角色模糊化管理（PM 写代码、工程师做内容设计）

### 3. 组织形态

- **尽量扁平**：一个整体使命，不为每个 pod 单独设使命（避免频繁重组成本）
- **管理者先做 IC**：建立产品感和团队信任，重狗粮
- **不再以 10:1 比例衡量 IC/Manager**

### 4. 团队构成

索引两类工程师：
- **创造性构建者 + 产品感**：好奇心、迭代能力、用户感
- **深度系统专家**：分布式系统、基础设施等硬核能力

不再优先看重：原始编码吞吐量

### 5. Claude 化一切

> "What's better than one of us doing it? Having Claude."

- 识别"最嘈杂的工作流"，优先 Claudify
- 验证、triage、代码审查、日报摘要、onboarding 文档……
- 各 pod 自主决定先 Claudify 哪些流程

### 6. 效果衡量

- Onboarding 上手时间 ↓
- PR 周期时间 ↓（同时暴露 CI/基础设施瓶颈）
- Claude 辅助提交率 → 趋近 100%

---

## 开放问题

- 平台专属团队（iOS/Android）在角色模糊化后是否仍有价值？
- 全自动审查的边界随模型能力提升而动态变化 → 需要持续 re-evaluate
- 所有人都感到同等高效？（角色模糊化的公平感）

---

## 关联来源

- [[sources/fiona-fung-ai-native-engineering-2026-05-11]]
- [[sources/dario-daniela-amodei-conversation-2026-05-10]]（从另一角度印证了 Amdahl 定律在 AI 时代的应用）

---
type: concept
name: Plan-Execute 循环
domain: agentic-engineering
address: c-000594
created: 2026-06-05
updated: 2026-06-12
tags:
  - claude-code
  - workflow
  - planning
  - agentic-engineering
status: active
related:
  - "[[concepts/DynamicWorkflows]]"
  - "[[concepts/Loop机制]]"
  - "[[concepts/Grilling模式]]"
  - "[[concepts/JIT规划]]"
  - "[[MattVanHorn]]"
---

# Plan-Execute 循环

Matt Van Horn 推广的 Agentic Engineering 核心工作流：将每一次 Agent 交互拆分为**计划（Plan）**和**执行（Work）**两个独立阶段，通过 Compound Engineering 插件（`/ce-plan` → `/ce-work`）驱动。

## 核心流程

```
想法 → /ce-plan → plan.md → /ce-work → 结果
  ↑                                    |
  └──────── 反馈/重定向 ←───────────────┘
```

### Plan 阶段（`/ce-plan`）

Agent 并行 fan-out 研究：
- 阅读代码库找模式和约定
- 搜索历史方案
- 研究外部文档和最佳实践

输出结构化 `plan.md`：问题定义 → 方案 → 涉及文件 → 验收标准（checkbox）→ 代码模式参考。

### Execute 阶段（`/ce-work`）

Agent 按 `plan.md` 逐步构建。上下文溢出时→新 session 指向计划→续传。

## 关键洞察

### 1. 不用读计划
计划是给 Agent 的，不是给人类的。直接 `/ce-work`，有问题就问 "TLDR?" 或 "eli5 this plan"。

### 2. Plan for the plan
对抗 Agentic Laziness 的最强技巧：让 Agent 先规划**如何产出**再执行。适用于代码、策略文档、竞品分析等所有任务。

> 与 [[concepts/Grilling模式]] 收敛：两者都是通过强制 Agent 先"思考再行动"来防止偷懒。

### 3. 翻转传统比例
传统开发 ~80% 编码 + 20% 规划 → Plan-Execute 翻转此比例。计划是"活过一切的检查点"。

### 4. 计划复利
每个 `plan.md` 保留在知识库中→未来计划质量逐步提升。→ 与 [[concepts/代码仓库即记录系统]] 收敛。

## 适用场景

不仅限于代码：
- 策略文档
- 产品规格
- 竞品分析
- 董事会更新
- 开源贡献（数百 PR 用此模式合并进 Python/Go/OpenCV）

## 与 Dynamic Workflows 的关系

Plan-Execute 是 **Fan-out-and-synthesize**（Plan 阶段） + **Loop until done**（Execute 阶段）的组合实例。Compound Engineering 插件是 Dynamic Workflows 的固定化封装。→ [[concepts/DynamicWorkflows]]

## 工具

- **Compound Engineering 插件**：`/ce-plan` `/ce-work` `/ce-brainstorm`
- **last30days**：研究阶段前置，提供社区最新知识
- **Proof**：将 `plan.md` 渲染为可读文档，评论回流 Agent loop

## 来源

- [[sources/matt-vanhorn-agentic-hacks-2026-06-05|Every Agentic Engineering Hack I Know (June 2026)]]（Matt Van Horn，2026-06-02）

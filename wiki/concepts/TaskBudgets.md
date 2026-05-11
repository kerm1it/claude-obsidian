---
type: concept
address: c-000058
title: "Task Budgets（任务预算）"
created: 2026-05-11
updated: 2026-05-11
tags:
  - task-budgets
  - effort
  - anthropic
  - agent-control
status: active
related:
  - "[[concepts/EffortDial]]"
  - "[[concepts/TestTimeCompute]]"
  - "[[sources/the-thinking-lever-2026-05-11]]"
---

# Task Budgets（任务预算）

**来源**：[[sources/the-thinking-lever-2026-05-11]]，[[people/MattBleifer]]（Anthropic）

---

## 是什么

Task Budgets 是 Anthropic 新发布的功能：用户为 Claude 设置一个 token 花费的**硬上限**，到达上限前 Claude 主动停下来向用户 check-in。

预算单位：
- Token 数量（如"不超过 100,000 tokens"）
- 时间
- 成本

---

## 为什么重要

随着 Claude 开始运行**数天、数周乃至数月**的长期任务，"无限运行直到完成"变得不可接受：
- 成本不可预测
- 方向偏差难以纠正
- 需要人类在关键节点介入

Task Budgets 提供了一个结构化的"人类检查点"机制，与 [[concepts/AgentMemoryAPI]] 中的多 Agent 控制需求高度一致。

---

## 与 Effort 的关系

- **Effort**：表达质量/速度偏好（相对控制）
- **Task Budgets**：设置硬上限（绝对控制）

两者配合使用：先用 Effort 告诉 Claude 怎么分配，再用 Budget 确保不超出可接受范围。

---

## 关联

- [[concepts/EffortDial]] — 配套的相对控制接口
- [[concepts/AgentMemoryAPI]] — 长期 Agent 任务的记忆管理

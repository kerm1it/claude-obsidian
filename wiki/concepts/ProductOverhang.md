---
address: c-000068
type: concept
title: "Product Overhang（产品过剩）"
created: 2026-05-12
updated: 2026-05-12
tags:
  - anthropic
  - product-strategy
  - agent
status: active
related:
  - "[[concepts/ExpandingToolkit]]"
  - "[[people/BorisCherny]]"
  - "[[domains/Claude-Code]]"
---

# Product Overhang（产品过剩）

**来源：** [[people/BorisCherny]]（Claude Code 创始人，Anthropic）  
**参见：** [[sources/boris-cherny-coding-solved-2026-05-12]]

---

## 定义

> "模型能做的，远超任何已有产品所能捕捉的。"

**Product Overhang（产品过剩）**：模型能力已经存在，但还没有对应产品来充分释放这些能力的状态。识别并填补这个缺口，就是正确的建造时机。

---

## Claude Code 的案例

- 2024 年底，SoTA 产品只有"按 Tab 补全一行代码"
- 但模型能力已经可以支撑 Agent 写全部代码
- Boris 识别到这个 overhang → 开始构建 Claude Code
- **前六个月产品不好用**，因为是为"下一个模型"构建的
- 指数增长始于 Opus 4（2026 年 5 月）——模型赶上了产品

---

## 策略含义

**核心策略**：找到模型能力已存在、但产品尚未捕捉的空白，提前建造，等待模型赶上。

- 需要接受短期 PMF 缺失（"我们知道六个月内不会有 PMF"）
- 要求对模型能力的前瞻判断
- **被时间验证**：Claude Code 的每次模型升级（4.5 → 4.6 → 4.7）都带来新的增长拐点

---

## 当前的 Product Overhang 方向（Boris 2026 年指出）

- **Claude Design**：今天还不够好，但模型会越来越好
- **/loop + /batch**：大规模并行 Agent，正在成熟
- **Computer Use**：今天可用但慢，能力在快速提升

---

## 与相关概念的关系

- [[concepts/ExpandingToolkit]]（Lucas）：脚手架随模型出货——是 Product Overhang 被填补后的结果
- [[concepts/NativeResolutionComputerUse]]：Computer Use 的 Overhang 正在被 Opus 4.7 填补

---

## 来源

- [[sources/boris-cherny-coding-solved-2026-05-12]]

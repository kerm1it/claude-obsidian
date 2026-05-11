---
address: c-000041
type: concept
title: "JIT 规划（Just-In-Time Planning）"
created: 2026-05-11
updated: 2026-05-11
tags:
  - planning
  - agile
  - ai-native
  - management
status: active
related:
  - "[[concepts/AI原生工程组织]]"
  - "[[concepts/瓶颈转移论]]"
  - "[[people/FionaFung]]"
---

# JIT 规划（Just-In-Time Planning）

**提出者：** [[people/FionaFung]]，类比 JIT 编译（Just-In-Time Compilation）

---

## 定义

在 AI 原生工程环境中，由于原型构建和代码生成不再是瓶颈，长期详细规划的 ROI 大幅下降。JIT 规划指：**只在需要时做足够的规划，而不是提前规划所有细节**。

---

## 背景

Fiona Fung 加入 Claude Code 团队后尝试制定六个月路线图。三个月后，内容就已大幅过时。这说明：

- 在高变化率环境下，六个月路线图的有效期不足三个月
- 规划成本（时间）并未随 AI 的引入而降低，但规划的必要精度已下降
- 与其精细预测未来六个月，不如快速原型验证当下假设

---

## 实践

Claude Code 团队的做法：
- **减少**：多轮产品评审、事先详尽的设计文档
- **代替**：PR 即讨论（idea → prototype → PR，而非 idea → spec → review → code）
- **加速**：内部大规模 dogfooding → 外部用户反馈 → 快速迭代

---

## 适用条件

JIT 规划在以下情况效果好：
- 变化速率高（技术/市场快速演进）
- 原型成本低（AI 大幅降低构建成本）
- 团队具备良好的技术对齐文化（防止"最晚提交者赢"的竞速问题）

在以下情况仍需传统规划：
- 合规/法务要求明确的里程碑
- 大型跨团队依赖需要协调
- 重大架构决策（需要设计文档）

---

## 关联

- [[concepts/AI原生工程组织]] — JIT 规划是其中的规范重写之一
- [[concepts/瓶颈转移论]] — 规划减少的根本原因
- [[sources/fiona-fung-ai-native-engineering-2026-05-11]]

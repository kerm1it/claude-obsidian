---
type: concept
address: c-000151
title: "Agent 评估体系（Agent Eval System）"
created: 2026-05-26
updated: 2026-05-26
tags:
  - evals
  - agent-evaluation
  - anthropic
  - engineering
status: active
related:
  - "[[concepts/非确定性评测指标]]"
  - "[[concepts/Eval驱动开发]]"
  - "[[concepts/模型即产品]]"
  - "[[sources/anthropic-demystifying-evals-agents-2026-05-26]]"
---

# Agent 评估体系（Agent Eval System）

**来源**：[[sources/anthropic-demystifying-evals-agents-2026-05-26]]  
**出处**：Anthropic Engineering Blog

---

## 核心思想

> "Without evals, teams operate reactively, discovering issues only in production."

Agent eval 是从"被动发现问题"到"主动把控质量"的基础设施。早期投入创造复利价值。

---

## 评分方式三层

| 类型 | 方法 | 适用场景 |
|------|------|---------|
| **代码评分** | 字符串匹配、测试通过/失败、静态分析、状态检查 | 编码 agent、有确定性结果的任务 |
| **模型评分** | Rubric、自然语言断言、对比评分、多评判共识 | 开放性任务、交互质量、研究质量 |
| **人工评分** | SME 审查、众包、抽样 | 黄金标准，校准模型评分器 |

实践原则：**优先确定性 grader → 必要时 LLM grader → 谨慎人工 grader**

---

## 评测类型

```
能力 Eval（低通过率）
  ↓ 随改进提升
  ↓ 接近饱和时
回归 Eval（~100% 通过率）
  ↓ 持续运行
  ↓ 防止性能下滑
```

---

## 四类 Agent 的 Eval 设计

### 编码 Agent
- 核心：单元测试通过/失败（确定性）
- 补充：transcript 分析代码质量、工具使用
- Benchmark：SWE-bench Verified、Terminal-Bench

### 对话 Agent
- 核心挑战：评估交互质量，不只是最终结果
- 方法：终态验证 + rubric + 第二 LLM 模拟用户
- Benchmark：τ-Bench、τ2-Bench

### 研究 Agent
- 核心挑战："正确"和"全面"依赖上下文
- 方法：接地性检查 + 覆盖率检查 + 来源质量检查
- Benchmark：BrowseComp

### 计算机操作 Agent
- 核心：沙盒环境 + 状态检查验证结果
- Benchmark：WebArena（浏览器）、OSWorld（完整 OS）

---

## 从零建立 Eval 的关键原则

1. **早开始**：20-50 个真实失败案例足够启动
2. **任务无歧义**：两位专家独立评分应一致；包含参考解答
3. **干净环境**：每次 trial 从干净状态开始，避免相关失败
4. **评分路径，不评步骤**：agent 会找到 eval 设计者未预料的合法路径
5. **阅读 transcript**：失败时先读 transcript，区分真实错误 vs grader 误判
6. **监控饱和度**：100% 通过率 = 无改进信号

---

## 瑞士奶酪模型

没有单一 eval 层能捕获所有问题。多层组合：
- 自动化 eval（快速迭代）
- 生产监控（真实基准）
- A/B 测试（用户结果）
- 人工审查（校准）

---

## 关联概念

- [[concepts/非确定性评测指标]] — pass@k / pass^k 处理输出方差
- [[concepts/Eval驱动开发]] — eval-first 开发范式
- [[concepts/模型即产品]] — Research PM 如何用 eval 驱动模型改进
- [[concepts/自我改进AI循环]] — eval 是自我改进循环的质量门

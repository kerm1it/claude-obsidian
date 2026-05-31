---
type: source
address: c-000150
title: "Demystifying Evals for AI Agents"
created: 2026-05-26
updated: 2026-05-26
tags:
  - anthropic
  - evals
  - agent-evaluation
  - engineering
status: active
related:
  - "[[entities/Anthropic]]"
  - "[[concepts/Agent评估体系]]"
  - "[[concepts/非确定性评测指标]]"
  - "[[concepts/Eval驱动开发]]"
  - "[[concepts/模型即产品]]"
  - "[[concepts/LLMJudgeAIFeedbackCalibration边界]]"
  - "[[concepts/EvalResultInterpretationDecisionThreshold边界]]"
---

# Demystifying Evals for AI Agents

**来源**：Anthropic Engineering Blog
**链接**：https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents
**发布**：2026 年 5 月
**作者**：Anthropic Engineering

---

## 摘要

Anthropic 工程团队系统梳理 AI Agent 评估（Eval）的完整体系：从术语定义、评分方式、评测类别，到四类 Agent（编码/对话/研究/计算机操作）的具体 eval 策略，再到从零建立 Eval 的实践路线图。核心观点：没有 eval 的团队陷入被动循环；早期投入 eval 创造复利价值。

---

## 核心术语

| 术语 | 定义 |
|------|------|
| **Task/Test Case** | 单个测试，包含输入和成功标准 |
| **Trial** | 对一个任务的一次执行（多次运行应对输出方差）|
| **Grader** | 评分逻辑；一个任务可有多个 grader |
| **Transcript/Trace** | 完整记录：输出 + 工具调用 + 推理过程 |
| **Outcome** | 最终环境状态（区别于 agent 声称的状态）|
| **Eval Harness** | 并发运行 eval 的基础设施 |
| **Evaluation Suite** | 评测特定能力的任务集合 |

---

## 三类评分方式

### 代码评分（Code-Based Graders）
- 方法：字符串匹配、二元测试、静态分析、状态验证、工具调用验证
- 优：快、便宜、客观、可复现
- 缺：对合法变体脆弱，缺乏细腻度

### 模型评分（Model-Based Graders）
- 方法：Rubric 评分、自然语言断言、对比评分、参考评分、多评判共识
- 优：灵活、可扩展、处理开放性任务
- 缺：非确定性、贵、需与人类评分校准；在高风险用途上需要 human anchor、bias check 和 transcript review

### 人工评分（Human Graders）
- 方法：SME 审查、众包、抽样、A/B 测试、标注者一致性
- 优：黄金标准，校准模型评分器
- 缺：贵、慢，规模化困难

---

## 评测类型

- **能力/质量 Eval**：从低通过率开始，目标是难任务，引导改进方向
- **回归 Eval**：维持 ~100% 通过率，防止性能下滑
- 能力 eval 通过率提升后"毕业"进入持续运行的回归套件

---

## 四类 Agent 的 Eval 策略

### 编码 Agent
- 依赖确定性评分（代码要么通过测试，要么不通过）
- 示例 benchmark：SWE-bench Verified（修复 Python 仓库问题）、Terminal-Bench
- 组合：单元测试验证（结果）+ transcript 分析（代码质量、工具使用模式）

### 对话 Agent（客服/销售/辅导）
- 挑战：评估交互质量本身，不只是最终结果
- 方法：可验证的终态结果 + rubric（任务完成 + 交互质量）+ 第二个 LLM 模拟用户
- 示例 benchmark：τ-Bench、τ2-Bench

### 研究 Agent
- 挑战："全面"和"正确"依赖具体任务上下文；专家可能不一致；长输出 = 更多失败点
- 策略：接地性检查（claim 有来源支撑）+ 覆盖率检查（必须包含的事实）+ 来源质量检查
- 示例 benchmark：BrowseComp

### 计算机操作 Agent
- 评估方法：在真实或沙盒环境中运行，通过状态检查验证预期结果
- 示例 benchmark：WebArena（浏览器任务）、OSWorld（完整 OS 控制）
- 权衡：DOM 交互（token 多、速度快）vs 截图交互（token 少、速度慢）

---

## 非确定性评测指标

参见：[[concepts/非确定性评测指标]]

- **pass@k**：k 次尝试中至少成功一次的概率；k 大 → 分数高
- **pass^k**：k 次尝试**全部**成功的概率；k 大 → 分数低
- 使用场景：pass@k 用于容忍一次成功的工具；pass^k 用于面向客户需要一致可靠的 agent

---

## 从零建立 Eval 的路线图

1. **从 20-50 个真实失败案例开始**，不要等待完美数据集
2. **任务要无歧义**：两位领域专家独立评分应一致；包含参考解答证明任务可完成
3. **基础设施健壮性**：每次 trial 从干净环境开始；避免共享状态导致相关失败
4. **评分策略**：优先确定性 grader → 必要时 LLM grader → 谨慎使用人工 grader
5. **评分路径，不评步骤**：agent 会找到 eval 设计者未预料到的合法路径
6. **阅读 transcript**：任务失败时 transcript 揭示是真实错误还是 grader 误判
7. **监控饱和度**：100% 通过率的 eval 无改进信号；SWE-Bench 从 30% 升至 80%+
8. **Eval 驱动开发**（[[concepts/Eval驱动开发]]）：先建 eval 定义计划能力，再迭代直到通过

---

## Eval 的瑞士奶酪模型

> "No single evaluation layer catches every issue. With multiple methods combined, failures that slip through one layer are caught by another."

| 方法 | 优势 | 劣势 |
|------|------|------|
| 自动化 eval | 快速迭代、可复现、每次提交运行 | 需要前期投入、可能产生虚假自信 |
| 生产监控 | 真实用户行为、真实基准 | 被动响应、信号嘈杂 |
| A/B 测试 | 衡量真实用户结果 | 慢（天/周）|
| 用户反馈 | 暴露意外问题 | 稀疏、偏向严重问题 |
| 人工 transcript 审查 | 建立直觉，发现细微问题 | 耗时、不可扩展 |
| 系统性人类研究 | 黄金标准 | 昂贵、需专家 |

---

## Eval 设计陷阱（真实案例）

- **Opus 4.5 在 CORE-Bench 初始评分 42%**：原因是严格评分（"96.12" vs "96.124991..."）、模糊规格、随机性任务
- **METR 时间视野 benchmark**：要求优化到阈值，但评分需要**超过**阈值，惩罚了遵循指令的模型
- **教训**：仔细双检查任务和 grader；在信任分数前阅读多份 transcript

---

## Eval 框架

Harbor、Braintrust、LangSmith、Langfuse、Arize Phoenix — 框架加速进度，但"只有你运行的 eval 任务质量一样好"。

---

## 关联概念

- [[concepts/Agent评估体系]] — 完整体系页面
- [[concepts/非确定性评测指标]] — pass@k / pass^k
- [[concepts/Eval驱动开发]] — eval-first 开发范式
- [[concepts/模型即产品]] — Alex Albert 的 eval 视角在此深化

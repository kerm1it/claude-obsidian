---
address: c-000171
type: concept
title: "AI 系统生成链"
created: 2026-05-30
updated: 2026-05-30
tags:
  - ai
  - taxonomy
  - systems-thinking
status: active
related:
  - "[[domains/AI知识体系]]"
  - "[[learning/AI体系学习路线]]"
  - "[[concepts/上下文工程]]"
  - "[[concepts/Agent评估体系]]"
  - "[[concepts/自我改进AI循环]]"
sources:
  - "[[Research: AI知识体系总览]]"
---

# AI 系统生成链

AI 系统生成链是一种稳定分类法：把 AI 知识放进“能力如何产生、如何接入任务、如何行动、如何评估、如何改进”的连续链路中，而不是按流行词分堆。

## 核心定义

AI 系统 = 模型能力 + 上下文接入 + 工具行动 + 评估反馈 + 产品/组织闭环。

链路：

`基础理论 → 模型构建 → 推理能力 → 上下文与知识 → Agent 系统 → 评估可靠性 → 产品组织 → 自我改进`

自我改进不是终点，而是反馈环：它把真实运行中的失败、偏好、数据、trace 和流程瓶颈重新喂回模型构建、上下文设计、工具设计和 eval。

## 分类规则

| 判断问题 | 如果答案是 | 主归属 |
|---|---|---|
| 它解释能力为什么会出现吗？ | 架构、优化、规模、表示 | 基础理论层 |
| 它改变模型权重吗？ | pretrain、fine-tune、RLHF、distill | 模型构建层 |
| 它发生在模型运行时吗？ | reasoning、TTC、多模态、serving | 推理与能力层 |
| 它给模型提供任务现场知识吗？ | prompt、context、RAG、memory、skill | 上下文与知识层 |
| 它让模型调用工具或改变环境吗？ | loop、tool use、workflow、harness | Agent 系统层 |
| 它判断系统好坏或控制风险吗？ | eval、benchmark、monitoring、guardrail | 评估与可靠性层 |
| 它把能力嵌入业务或组织吗？ | product、workflow、company brain | 产品与组织层 |
| 它用运行结果改进系统吗？ | dream、self-improvement、autonomous research | 自我改进与前沿层 |

## 容易误放的概念

- **prompt engineering**：不是基础理论，主归属是上下文与知识层。
- **context engineering**：不是 prompt 的换名，而是多轮任务中对全部 token、工具、记忆和历史的管理。
- **fine-tuning**：主归属是模型构建层；只有当讨论“是否值得改权重”时，才和上下文层比较。
- **RAG**：主归属是上下文与知识层；它把外部知识放进运行时，而不是默认改变模型。
- **harness**：主归属是 Agent 系统层；它把模型、工具、状态、文件、沙盒和 trace 组织成运行时。
- **eval**：主归属是评估与可靠性层；它的结果会反哺产品、上下文和模型。
- **dream / self-improvement**：主归属是自我改进层；没有日志、eval 和可执行改动时只是愿景。

## 反馈环

最小自我改进环：

1. Agent 执行任务，留下 trace、工具调用、产物和失败。
2. Eval 或人工审查判定失败类型。
3. 系统把失败转成新测试、新上下文规则、新工具说明、新 skill 或新训练数据。
4. 下一轮运行验证是否改善。

这个闭环同时连接：
- [[concepts/上下文工程]]：把失败转成更好的上下文选择。
- [[concepts/Agent评估体系]]：把失败转成可回归的 eval。
- [[concepts/Skillify]]：把一次性修复固化为 skill。
- [[concepts/自我改进AI循环]]：把局部改进扩展成组织级闭环。

## 使用方式

当看到新概念时，先写一行：

`概念名 → 主层级 → 上游输入 → 下游输出 → 评估方式 → 可能反哺`

如果这一行写不出来，先不要扩层级；把它放到 [[domains/AI知识体系#待归类 / 边界概念]]。

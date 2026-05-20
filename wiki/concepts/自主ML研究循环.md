---
type: concept
address: c-000129
title: "自主 ML 研究循环"
aliases:
  - Autonomous ML Research Loop
  - autoresearch loop
created: 2026-05-20
tags:
  - ai-agents
  - ml-training
  - research-automation
  - karpathy
status: active
related:
  - "[[concepts/程序驱动研究]]"
  - "[[concepts/固定时间窗实验]]"
  - "[[entities/Autoresearch]]"
  - "[[people/AndrejKarpathy]]"
---

# 自主 ML 研究循环

## 定义

AI agent 自主执行机器学习实验的闭环模式：**修改代码 → 训练 → 评估指标 → 决策下一步 → 循环**，无需人类介入中间步骤。

## 核心机制

```
program.md（人类设定目标/约束）
     ↓
Agent 读取指令
     ↓
修改 train.py（架构/超参/优化器）
     ↓
固定时间窗训练（5 分钟）
     ↓
读取 val_bpb 指标
     ↓
决策：保留/回滚/继续探索
     ↓
循环（过夜 ≈ 100 次）
```

## 关键设计约束

1. **固定时间窗**：5 分钟 wall clock，排除启动时间 → 跨实验可比（见 [[concepts/固定时间窗实验]]）
2. **单一指标**：val_bpb（bits-per-byte），词表大小无关
3. **单文件编辑范围**：agent 只改 `train.py`，diff 可审查
4. **指令分离**：研究目标写在 `program.md`（人类域），代码改动在 `train.py`（agent 域）

## 与传统 ML 研究对比

| 维度 | 传统方式 | 自主循环 |
|------|----------|----------|
| 实验速度 | 人工启动，等结果，分析，重复 | 过夜 100 次，并行探索 |
| 干预粒度 | 每次实验人工决策 | Agent 自主决策，人类只设目标 |
| 硬件要求 | 通常多 GPU | 单 GPU（H100） |
| 可审查性 | 完整控制 | diff 可读，但 agent 推理不透明 |

## 参考实现

- [[entities/Autoresearch]]（karpathy/autoresearch，82.2k ⭐）

## 相关概念

- [[concepts/程序驱动研究]] — program.md 作为研究接口
- [[concepts/固定时间窗实验]] — 5 分钟 budget 的具体机制
- [[concepts/Loop机制]] — Claude Code 中的类似循环思想
- [[concepts/JIT规划]] — agent 实时规划与自主决策的交集

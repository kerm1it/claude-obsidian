---
type: entity
address: c-000127
title: "Autoresearch"
entity_type: open-source-repo
created: 2026-05-20
tags:
  - github
  - ml-training
  - autonomous-agents
  - karpathy
status: active
related:
  - "[[people/AndrejKarpathy]]"
  - "[[concepts/自主ML研究循环]]"
  - "[[concepts/程序驱动研究]]"
  - "[[concepts/固定时间窗实验]]"
  - "[[sources/autoresearch-2026-05-20]]"
---

# Autoresearch

**类型：** 开源 GitHub 仓库  
**URL：** https://github.com/karpathy/autoresearch  
**作者：** [[people/AndrejKarpathy]]  
**规模：** 82.2k ⭐（截至 2026-05-20）  
**语言：** Python + Jupyter Notebook

## 一句话

让 AI agent 过夜自主跑机器学习实验：改代码 → 5 分钟训练 → 评估 val_bpb → 迭代，循环约 100 次。

## 核心设计

- **单文件接口**：agent 只改 `train.py`，人类只改 `program.md`
- **固定时间窗**：每次实验 5 分钟，跨实验可直接比较
- **极简依赖**：PyTorch + uv，无分布式训练
- **单 GPU**：H100 测试，社区 fork 支持 Mac/Windows/AMD

## 历史背景

Karpathy 在 nanoGPT / nanoChatGPT 系列之后推出，将"程序员控制实验"演变为"agent 控制实验"。是 [[concepts/自主ML研究循环]] 模式的参考实现。

## 关联来源

- [[sources/autoresearch-2026-05-20]]

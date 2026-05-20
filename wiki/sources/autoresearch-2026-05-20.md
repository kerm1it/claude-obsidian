---
type: source
address: c-000126
title: "autoresearch — Karpathy 自主 ML 研究循环（2026-05-20）"
source_url: https://github.com/karpathy/autoresearch
source_type: github-repo
author: "[[people/AndrejKarpathy]]"
fetched: 2026-05-20
created: 2026-05-20
tags:
  - ai-research
  - autonomous-agents
  - ml-training
  - karpathy
  - github
status: active
related:
  - "[[entities/Autoresearch]]"
  - "[[people/AndrejKarpathy]]"
  - "[[concepts/自主ML研究循环]]"
  - "[[concepts/程序驱动研究]]"
  - "[[concepts/固定时间窗实验]]"
---

# autoresearch — Karpathy 自主 ML 研究循环

**来源：** https://github.com/karpathy/autoresearch  
**作者：** [[people/AndrejKarpathy]]  
**规模：** 82.2k ⭐，Python 83.4% + Jupyter 16.6%

## 核心主张

> [!key-insight] 一句话
> 把 AI agent 接入训练循环，让它过夜自主跑百次实验、改代码、评估结果——研究员早上醒来收获实验日志与更优模型。

研究员不再手写 Python，而是编辑 **`program.md`**（Markdown 指令文件）来告诉 agent 该做什么。Agent 负责修改 `train.py`、启动训练、读取指标、决定下一步。

## 系统架构

### 核心三文件

| 文件 | 归属 | 功能 |
|------|------|------|
| `prepare.py` | 人类写，不改动 | 常量、数据下载、BPE tokenizer 训练、工具函数 |
| `train.py` | **Agent 编辑** | 完整 GPT 模型 + Muon/AdamW 优化器 + 训练循环 |
| `program.md` | **人类编辑** | Agent 的指令文件，类似"超轻量 skill" |

### 评估指标

**val_bpb**（validation bits-per-byte）：更低 = 更好。与词表大小无关，跨架构变体可直接比较。

### [[concepts/固定时间窗实验|固定 5 分钟时间窗]]

- 每次实验：固定 5 分钟墙钟时间（排除启动），确保可比性
- 速率：约 12 次实验 / 小时，过夜约 100 次实验
- Agent 只改 `train.py`，diff 可审查

## 使用方法

```bash
# 1. 安装 uv
curl -LsSf https://astral.sh/uv/install.sh | sh

# 2. 同步依赖
uv sync

# 3. 准备数据/tokenizer（约 2 分钟）
uv run prepare.py

# 4. 测试单次实验（约 5 分钟）
uv run train.py
```

启动 agent 会话：
> "Hi have a look at program.md and let's kick off a new experiment! let's do the setup first."

## 设计哲学

"No external dependencies beyond PyTorch and a few small packages. No distributed training, no complex configs. **One GPU, one file, one metric.**"

极简主义：无分布式训练、无复杂配置，单 GPU、单文件、单指标。

## 硬件要求

- 单 NVIDIA GPU（H100 测试通过）
- Python 3.10+
- uv 包管理器

## 社区衍生

MacOS、Windows、AMD GPU 平台适配版本均由社区 fork 实现。

## 关联概念

- [[concepts/自主ML研究循环]] — 核心模式：agent 在固定时间窗内循环改代码→训练→评估
- [[concepts/程序驱动研究]] — program.md 作为研究接口的设计模式
- [[concepts/固定时间窗实验]] — 5 分钟 budget 保证跨实验可比性
- [[concepts/ScalingLaws]] — val_bpb 指标与 scaling 研究传统一脉相承

## Extraction Notes

- README 通过 WebFetch 从主仓库页面提取；raw GitHub 文件 URL 返回 404（仓库可能设有访问限制）
- `program.md` 内容无法直接获取，描述来自 README 间接引用

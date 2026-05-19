---
address: c-000120
type: entity
entity_type: library
title: "RuVector"
created: 2026-05-19
updated: 2026-05-19
tags:
  - entity
  - library
  - signal-processing
  - edge-ai
status: active
related:
  - "[[entities/RuView]]"
  - "[[entities/CognitumSeed]]"
  - "[[people/ruvnet]]"
  - "[[concepts/CSI感知]]"
  - "[[concepts/自监督WiFi学习]]"
---

# RuVector

**类型**：AI 骨干库 / 信号处理引擎
**仓库**：[github.com/ruvnet/ruvector](https://github.com/ruvnet/ruvector/)
**出品**：[[people/ruvnet]]

## 是什么

RuVector 是 [[entities/RuView]] 和 [[entities/CognitumSeed]] 共用的 AI 骨干。提供 CSI 信号的 attention 机制、图算法、压缩算法，以及对比学习嵌入层——是整个 WiFi 感知栈的信号处理基础。

## 核心组件

- **Attention 机制**：Flash Attention 子载波分组，识别空间焦点区域与熵
- **图算法**：PageRank 影响力图（4x4 互相关），Multi-Person 匹配（匈牙利算法精简版）
- **压缩算法**：三层自适应量化（8-bit 热 / 5-bit 温 / 3-bit 冷）
- **对比学习嵌入**：→ [[concepts/自监督WiFi学习]]，输出 128 维环境指纹
- **RVF 格式**：可解析/序列化至 Cognitum Seed 向量存储的容器格式

## 在系统中的位置

```
CSI 数据 → RuVector（信号处理 + 嵌入）
               ├─ 128 维环境指纹 → CognitumSeed（存储 + kNN）
               └─ 17 关键点姿态向量 → WiFlow 姿态解码器
```

## 发布

- crates.io：`wifi-densepose-ruvector`

## 参考素材

- [[sources/ruview-2026-05-19]]

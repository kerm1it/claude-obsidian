---
address: c-000124
type: concept
title: "WASM 边缘模块（no_std Rust on ESP32）"
created: 2026-05-19
updated: 2026-05-19
tags:
  - concept
  - edge-ai
  - wasm
  - esp32
  - rust
status: active
related:
  - "[[concepts/CSI感知]]"
  - "[[concepts/WiFiDensePose]]"
  - "[[entities/RuView]]"
  - "[[entities/RuVector]]"
---

# WASM 边缘模块（no_std Rust on ESP32）

## 核心思想

RuView 的 65 个边缘模块全部用 **no_std Rust** 编写，编译为 `wasm32-unknown-unknown`，通过 **WASM3** 解释器在 ESP32-S3 上执行——无需 Linux、无需 OS、无需云端，所有感知 AI 在 $9 传感器上就地运行。

## 架构模式

```
no_std Rust 模块源码
    ↓ 编译（cargo build --target wasm32-unknown-unknown）
WASM32 字节码（~几 KB/模块）
    ↓ OTA 部署到 ESP32-S3
WASM3 解释器（运行在 FreeRTOS 上）
    ↓ 12 函数 API（统一 host↔wasm 接口）
CSI 数据输入 → 感知输出
```

## 12 函数 Host API

所有模块共享同一套 host↔wasm 接口（12 个函数），实现模块热插拔——无需重新烧录固件。

## 65 个模块分类

| 类别 | 数量 | 时延预算 |
|------|------|---------|
| 信号智能 | 6 | S(<5ms) / L(<2ms) / H(<10ms) |
| 自适应学习 | 4 | S~H |
| 空间推理 | 3 | S |
| 时序分析 | 3 | S |
| AI 安全 | 2 | L~S |
| 量子启发 | 2 | S |
| 自主系统 | 2 | S |
| 医疗健康 | 5 | S |
| 安防安全 | 5 | S |
| 智能建筑 | 5 | S |
| 零售商业 | 5 | S |
| 工业专用 | 5 | S |
| 实验研究 | 10+ | S |

全部 1,463 个测试通过（2026-05-19）。

## 为什么 WASM + no_std

| 选择 | 理由 |
|------|------|
| no_std Rust | 无 OS 依赖，极小二进制，内存安全无 GC |
| WASM32 | 沙箱隔离，OTA 热更新模块，跨平台（ESP32 / Linux / 浏览器）|
| WASM3 解释器 | 针对嵌入式优化，RAM 仅需 ~64KB |

## 与云端 AI 的对比

| 维度 | WASM 边缘 | 云端 AI |
|------|-----------|---------|
| 延迟 | <2~10ms | 50~500ms |
| 隐私 | 数据不离设备 | 数据上传云端 |
| 离线能力 | 完全离线 | 需网络 |
| 成本 | 硬件一次性 | 按调用计费 |
| 部署 | OTA WASM 包 | 模型服务更新 |

## 扩展性

模块通过共同工具库（`vendor_common.rs`）共享基础能力；新模块只需实现 12 函数 API 即可接入，不触碰固件主体。

## 参考素材

- [[sources/ruview-2026-05-19]]

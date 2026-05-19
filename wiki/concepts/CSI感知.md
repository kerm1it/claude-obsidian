---
address: c-000122
type: concept
title: "CSI 感知（Channel State Information）"
created: 2026-05-19
updated: 2026-05-19
tags:
  - concept
  - wifi-sensing
  - signal-processing
  - physics
status: active
related:
  - "[[concepts/WiFiDensePose]]"
  - "[[concepts/WiFi生命体征监测]]"
  - "[[concepts/WASM边缘模块]]"
  - "[[entities/RuView]]"
---

# CSI 感知（Channel State Information）

## 是什么

Channel State Information（CSI）是 WiFi 物理层暴露的信道响应数据：描述无线信号在从发射端到接收端传播过程中的**幅度衰减**和**相位偏移**，精度到每个 OFDM 子载波（通常 56 个）。

## 物理直觉

每个 WiFi 路由器已经用无线电波填满你的空间。当人移动、呼吸、甚至静坐时，都会扰动这些波——哪怕只是胸腔 1mm 的起伏也会在 CSI 相位中留下可测量的痕迹。

```
发射端（路由器）→ 电磁波 → 人体/障碍物 → 多径反射/绕射 → 接收端（ESP32-S3）
                                                              ↓
                                            CSI：56 子载波 × [幅度, 相位]
```

## CSI vs RSSI

| 指标 | 粒度 | 信息量 | 用途 |
|------|------|--------|------|
| RSSI（信号强度）| 单值 | 极低 | 粗略存在检测 |
| CSI | 56 个子载波 × 幅度/相位 | 高 | 姿态、生命体征、活动识别 |

> 消费级 WiFi 笔记本仅提供 RSSI，无完整 CSI。

## CSI 能感知什么

| 信号频段 | 人体现象 | 可检测信息 |
|----------|----------|-----------|
| 0.1-0.5 Hz | 胸腔呼吸运动 | 呼吸率（6-30 BPM）|
| 0.8-2.0 Hz | 心搏微运动 | 心率（40-120 BPM）|
| >2 Hz | 肢体运动 | 步态、手势、姿态关键点 |
| DC 变化 | 空间遮挡 | 存在/占位/计数 |

## 硬件要求

**可采集完整 CSI 的硬件**：
- ESP32-S3（$9，推荐）
- Intel 5300 NIC（3x3 MIMO，研究级）
- Atheros AR9580
- Raspberry Pi 5/4（nexmon_csi patch，via rvcsi）

**不支持**：ESP32-C3、原版 ESP32（单核，CSI DSP 算力不足）

## 在 RuView 中的处理流程

```
ESP32-S3 采集 → CSI 帧（56 子载波）
    ↓
预处理（相位解绕、线性拟合去除 STO/CFO 偏差）
    ↓
RuVector 特征提取（Transformer + GNN）
    ↓
    ├─ 生命体征带通滤波（→ 呼吸/心率）
    ├─ 17 关键点姿态（→ WiFlow 解码器）
    └─ 128 维环境指纹（→ CognitumSeed 存储）
```

## 挑战与局限

- **单节点空间分辨率有限**：建议 2+ 节点或搭配 Cognitum Seed
- **穿墙深度**：~5m，受墙体材料影响
- **干扰**：高密度 WiFi 环境（办公室）信噪比下降
- **无摄像头姿态精度**：PCK@20 ≈ 2.5%（代理标签），远低于视觉方案

## 相关概念

- [[concepts/WiFiDensePose]]：CSI 上的人体姿态估计
- [[concepts/WiFi生命体征监测]]：CSI 上的呼吸/心率
- [[concepts/WASM边缘模块]]：运行在 ESP32 上的 CSI 处理模块
- [[concepts/自监督WiFi学习]]：无标签自适应新环境

## 参考素材

- [[sources/ruview-2026-05-19]]

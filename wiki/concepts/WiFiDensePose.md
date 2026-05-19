---
address: c-000121
type: concept
title: "WiFi DensePose（无摄像头人体姿态估计）"
created: 2026-05-19
updated: 2026-05-19
tags:
  - concept
  - wifi-sensing
  - pose-estimation
  - privacy
status: active
related:
  - "[[concepts/CSI感知]]"
  - "[[concepts/自监督WiFi学习]]"
  - "[[entities/RuView]]"
  - "[[entities/RuVector]]"
---

# WiFi DensePose（无摄像头人体姿态估计）

## 核心思想

WiFi DensePose 利用 Channel State Information（CSI）——即 WiFi 信号在多径传播中的幅度和相位信息——估计人体姿态，完全无需摄像头。理论基础：人体移动时扰动 WiFi 电磁场，这些扰动可被逆向解析为身体各部位的空间坐标。

起源：卡内基梅隆大学 *DensePose From WiFi* 研究。

## 工作原理

```
WiFi 信号（多径）
     ↓ 人体遮挡/反射
CSI 幅度 + 相位变化
     ↓ ESP32-S3 采集（56 子载波）
特征提取（RuVector：Transformer + 图神经网络）
     ↓
17 个 COCO 关键点坐标
```

## WiFlow 架构（RuView 实现）

- 输入：56 个 CSI 子载波的幅度/相位
- 骨干：Transformer + 图神经网络（双头输出）
- 输出 1：17 个关键点身体姿态（用于人体追踪）
- 输出 2：128 维环境指纹（用于检索 + 识别）
- 推理速度：171,000 嵌入/秒（M4 Pro）

## 精度现状（RuView，2026-05-19）

| 训练模式 | PCK@20 |
|----------|--------|
| 无摄像头（代理标签，10 传感器信号）| ≈ 2.5% |
| 摄像头监督（ADR-079 目标，待完成）| **35%+**（流水线已实现，评估阶段待完成）|

> [!note] 精度局限
> 无摄像头模式 PCK@20 仅 2.5%——当前实用价值有限，摄像头监督版本仍在开发中。

## 与传统方案对比

| 方案 | 优势 | 局限 |
|------|------|------|
| WiFi DensePose | 无摄像头、穿墙、低成本（$9/节点）、隐私保护 | 精度低于视觉方案 |
| 视觉姿态估计 | 高精度（MediaPipe PCK@20 70%+）| 需摄像头、强光、视线无遮挡 |
| 毫米波雷达 | 高精度、全天候 | 成本高（$50-300）|

## 隐私特性

WiFi DensePose 天然隐私友好：
- 无视频记录
- 无法识别面容
- 本地处理，无需云端
- 密封房间内的感知不被邻居感知（Fresnel 区域限制）

## 相关概念

- [[concepts/CSI感知]]：信号采集基础
- [[concepts/WiFi生命体征监测]]：同一 CSI 信号的生命体征提取
- [[concepts/自监督WiFi学习]]：无标签训练新环境

## 参考素材

- [[sources/ruview-2026-05-19]]

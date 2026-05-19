---
address: c-000123
type: concept
title: "WiFi 生命体征监测"
created: 2026-05-19
updated: 2026-05-19
tags:
  - concept
  - wifi-sensing
  - health
  - vital-signs
status: active
related:
  - "[[concepts/CSI感知]]"
  - "[[concepts/WiFiDensePose]]"
  - "[[entities/RuView]]"
---

# WiFi 生命体征监测

## 核心思想

通过对 CSI 信号进行**带通滤波 + 零交叉 BPM 计数**，可以非接触地测量人体呼吸率和心率——无需任何贴身传感器或摄像头，隔墙也能感知。

## 工作原理

人体两种微运动在 CSI 中留下不同频段的周期信号：

| 生理信号 | CSI 频段 | 检测方法 | 测量范围 |
|----------|----------|----------|----------|
| 呼吸 | 0.1–0.5 Hz | 带通滤波 → 零交叉计数 | 6–30 BPM |
| 心率 | 0.8–2.0 Hz | 带通滤波 → 零交叉计数 | 40–120 BPM |

```
CSI 原始信号
    ↓ 带通滤波（0.1-0.5 Hz）
呼吸波形 → 零交叉点 → BPM
    ↓ 带通滤波（0.8-2.0 Hz）
心跳波形 → 零交叉点 → BPM
```

## 医疗级边缘模块（RuView 实现）

[[concepts/WASM边缘模块]]中包含 5 个医疗场景模块，均运行于 ESP32-S3（<5ms 延迟）：

| 模块 | 功能 |
|------|------|
| `med_sleep_apnea.rs` | 检测睡眠中呼吸暂停 |
| `med_cardiac_arrhythmia.rs` | 监测心律不齐 |
| `med_respiratory_distress.rs` | 异常呼吸模式告警 |
| `med_gait_analysis.rs` | 步态追踪与异常检测 |
| `med_seizure_detect.rs` | 6 状态机识别强直阵挛性癫痫发作 |

另有 `exo_dream_stage.rs` 实现非接触睡眠分期（清醒/浅眠/深睡/REM）。

## 应用场景

- **居家养老监护**：老人跌倒、呼吸停止、心率异常
- **婴儿监护**：无摄像头呼吸监测
- **睡眠实验室替代**：整夜睡眠分期 + 呼吸暂停筛查，无需贴片
- **ICU 辅助监测**：通过病房 WiFi 实现非接触备份监测

## 局限性

- 单人测量为主；多人混叠时需算法分离
- 需要 ESP32-S3（带完整 CSI），消费级 WiFi 不支持
- 心率检测精度受运动干扰影响（胸腔大幅运动时呼吸信号掩盖心率信号）
- 未经医疗器械认证，当前为研究/消费级

## 相关概念

- [[concepts/CSI感知]]：底层信号基础
- [[concepts/WiFiDensePose]]：同一信号的姿态估计
- [[concepts/WASM边缘模块]]：运行在 ESP32 上的具体实现

## 参考素材

- [[sources/ruview-2026-05-19]]

---
address: c-000117
type: entity
entity_type: repo
title: "RuView"
created: 2026-05-19
updated: 2026-05-19
tags:
  - entity
  - repo
  - wifi-sensing
  - edge-ai
  - esp32
status: active
related:
  - "[[entities/CognitumSeed]]"
  - "[[entities/RuVector]]"
  - "[[people/ruvnet]]"
  - "[[concepts/WiFiDensePose]]"
  - "[[concepts/CSI感知]]"
  - "[[concepts/WASM边缘模块]]"
---

# RuView

**类型**：开源 GitHub 仓库 / WiFi 空间感知平台
**创作者**：[[people/ruvnet]]
**仓库**：[github.com/ruvnet/RuView](https://github.com/ruvnet/RuView)
**Stars**：59,973 ⭐ | **Forks**：7,814 | **语言**：Rust | **License**：MIT
**状态**：Beta（积极开发中）

## 是什么

RuView 把普通 WiFi 路由器变成穿墙空间感知系统。使用 $9 的 ESP32-S3 传感器采集 Channel State Information（CSI），无摄像头、无可穿戴设备，即可检测人员存在、测量生命体征、估计人体姿态。

## 核心能力

- 穿墙存在检测（最深 5m）
- 非接触呼吸（6-30 BPM）+ 心率（40-120 BPM）
- 17 关键点人体姿态估计（WiFlow 架构）
- 睡眠分期分类 + 呼吸暂停筛查
- 65 个边缘模块覆盖医疗、安防、零售、工业、研究等场景

## 技术栈

- **感知层**：ESP32-S3 CSI 流 → [[concepts/CSI感知]]
- **AI 骨干**：[[entities/RuVector]]
- **边缘运行时**：65 个 no_std Rust WASM 模块 → [[concepts/WASM边缘模块]]
- **持久记忆**：[[entities/CognitumSeed]]（$140 BOM，含 kNN + Ed25519 见证链）
- **rvCSI**：独立 RF 感知运行时（ruvnet/rvcsi）

## 相关概念

- [[concepts/WiFiDensePose]]：WiFi 无摄像头姿态估计原理
- [[concepts/CSI感知]]：Channel State Information 感知基础
- [[concepts/WiFi生命体征监测]]：呼吸与心率检测
- [[concepts/WASM边缘模块]]：边缘 AI 部署模式
- [[concepts/自监督WiFi学习]]：对比学习适应新环境

## Claude Code / Codex 插件

`plugins/ruview/`：9 skills，7 条 `/ruview-*` 命令，3 个 Agent；含 Codex 镜像。

## 参考素材

- [[sources/ruview-2026-05-19]]

---
address: c-000119
type: entity
entity_type: product
title: "Cognitum Seed"
created: 2026-05-19
updated: 2026-05-19
tags:
  - entity
  - hardware
  - edge-ai
  - vector-store
status: active
related:
  - "[[entities/RuView]]"
  - "[[entities/RuVector]]"
  - "[[people/ruvnet]]"
  - "[[concepts/CSI感知]]"
---

# Cognitum Seed

**类型**：边缘 AI 硬件伴侣
**网站**：[cognitum.one](https://cognitum.one)
**出品**：[[people/ruvnet]]
**总 BOM 成本**：~$140（含 ESP32-S3 节点）

## 是什么

Cognitum Seed 是 [[entities/RuView]] 的推荐硬件伴侣。在 ESP32-S3 传感器采集 CSI 数据后，Cognitum Seed 负责持久存储、向量检索和密码学认证，把临时感知数据变成可查询的长期空间记忆。

## 核心功能

- **持久向量存储（RVF）**：8 维特征向量存储，跨会话保留环境记忆
- **kNN 搜索**：快速最近邻检索，识别房间/活动/个人
- **Ed25519 见证链**：每次测量密码学签名，可验证、可追溯
- **MCP 代理**：通过 MCP 协议向 AI Agent 暴露传感数据接口
- **AI 集成**：与 [[entities/RuVector]] 深度集成，提供信号处理 + 记忆查询一体化

## 与 RuView 的关系

```
ESP32-S3 → CSI 流 → Cognitum Seed
                          ├─ 持久 RVF 向量存储
                          ├─ kNN 环境匹配
                          ├─ Ed25519 见证链
                          └─ MCP → AI Agent
```

## 部署选项

| 配置 | 硬件 | 成本 | 能力 |
|------|------|------|------|
| 推荐配置 | ESP32-S3 + Cognitum Seed | ~$140 | 完整：姿态、生命体征、运动 + 持久存储 + kNN + 见证链 |
| 纯 ESP32 Mesh | 3-6x ESP32-S3 | ~$54 | 姿态、生命体征、运动、存在 |
| 研究网卡 | Intel 5300 / Atheros AR9580 | ~$50-100 | 完整 CSI，3x3 MIMO |

## 参考素材

- [[sources/ruview-2026-05-19]]

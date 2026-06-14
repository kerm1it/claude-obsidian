---
type: entity
address: c-000082
title: "VibeVoice"
entity_type: open-source-model
url: https://github.com/microsoft/VibeVoice
created: 2026-05-14
updated: 2026-06-12
status: active
tags:
  - voice-ai
  - tts
  - asr
  - microsoft
  - speech-model
related:
  - "[[entities/Microsoft]]"
  - "[[concepts/下一令牌扩散]]"
  - "[[concepts/长音频单遍处理]]"
---

# VibeVoice

Microsoft Research 开源语音 AI 模型族，GitHub ⭐ 47,087，Python，MIT

## 核心参数

| 指标 | 数值 |
|---|---|
| Stars | 47,087 |
| 机构 | Microsoft Research |
| 基底模型 | Qwen2.5 |
| 发布时间 | 2025-08 ~ 2026-03 |
| 最高荣誉 | TTS：ICLR 2026 Oral |

## 模型家族

| 模型 | 用途 | 状态 |
|---|---|---|
| ASR-7B | 60分钟长音频识别，50+语言 | ✅ 可用（HF + Transformers） |
| TTS-1.5B | 90分钟多说话人合成 | ⚠️ 代码已下架（deepfake 滥用） |
| Realtime-0.5B | 实时流式 TTS，~300ms | ✅ 可用 |

## 技术特色

- **[[concepts/下一令牌扩散]]**：LLM（语义/上下文）+ 扩散头（声学保真度）混合架构
- **7.5 Hz 超低帧率令牌化**：序列压缩，支持[[concepts/长音频单遍处理]]
- **ASR 结构化输出**：Who + When + What（说话人+时间戳+内容）同时输出

## 来源

- [[sources/vibevoice-2026-05-14]]

---
type: source
address: c-000081
title: "VibeVoice — 开源前沿语音 AI 模型族"
source_type: github-repo
url: https://github.com/microsoft/VibeVoice
repo: microsoft/VibeVoice
stars: 47087
language: Python
license: MIT
ingested_at: 2026-05-14
tags:
  - voice-ai
  - tts
  - asr
  - speech
  - microsoft
related:
  - "[[entities/VibeVoice]]"
  - "[[entities/Microsoft]]"
  - "[[concepts/下一令牌扩散]]"
  - "[[concepts/长音频单遍处理]]"
---

# VibeVoice — 开源前沿语音 AI 模型族

microsoft/VibeVoice，GitHub，⭐ 47,087，Python，MIT

## 核心定位

Microsoft Research 开源的语音 AI 模型家族，涵盖 TTS（文本转语音）和 ASR（语音识别）。

**核心技术创新**：连续语音令牌化（Acoustic + Semantic 双令牌器），运行在超低帧率 **7.5 Hz**（对比传统 50+ Hz），大幅压缩序列长度，支持 60-90 分钟的单遍长音频处理。

架构：**[[concepts/下一令牌扩散]]**——LLM（Qwen2.5）理解文本上下文和对话流，扩散头生成高保真声学细节。

## 三款模型

### VibeVoice-ASR-7B — [[concepts/长音频单遍处理]]

发布：2026-01-21 | HuggingFace Transformers 集成：2026-03-06 | ICLR 2026

- **60 分钟单遍处理**：64K token 上下文窗口，无需切片，保持全局说话人追踪
- **结构化输出**：Who（说话人）+ When（时间戳）+ What（内容）——同时完成 ASR、说话人分离、时间戳标注
- **50+ 语言**：原生多语言支持
- **自定义热词**：可注入领域专有名词、特定名称提升识别准确率
- **vLLM 推理**：支持加速推理

**与本 vault 关联**：NotebookLM 转录 YouTube 音频的替代方案候选。

### VibeVoice-TTS-1.5B — 长音频多说话人 TTS

发布：2025-08-25 | ICLR 2026 Oral

- **90 分钟**长对话/单说话人语音，单遍生成
- **4 个说话人**，自然轮换，全程一致性
- 英文、中文、跨语言、即兴演唱
- ⚠️ **TTS 代码已于 2025-09-05 从仓库移除**：发现被用于深度伪造（deepfakes），违反使用意图，微软主动下架代码。HuggingFace 权重仍保留但 Web UI 已禁用。

### VibeVoice-Realtime-0.5B — 实时流式 TTS

发布：2025-12-03

- **~300ms 首次可听延迟**
- 流式文本输入（streaming text input）
- 0.5B 参数，部署友好
- 约 10 分钟稳定长音频生成
- 9 种语言 + 11 种英文风格声音

## 关键洞察

1. **7.5 Hz 超低帧率令牌化**：传统 ASR 切片 → 丢失全局上下文；VibeVoice 维持单一 64K context 处理整段音频，说话人追踪更准确
2. **LLM + 扩散头混合架构**：LLM 负责语义理解和对话流，扩散模型负责声学保真度——结合了两类模型各自的长处
3. **深度伪造风险导致代码下架**：微软主动移除 TTS 代码，体现了开源语音模型在负责任 AI 上的实际摩擦

## 技术规格

| 模型 | 参数量 | 上下文 | 延迟 |
|---|---|---|---|
| ASR-7B | 7B | 64K tokens（~60 分钟） | 离线 |
| TTS-1.5B | 1.5B | 90 分钟（已下架代码） | 离线 |
| Realtime-0.5B | 0.5B | ~10 分钟 | ~300ms |

## 风险与限制

基底模型：Qwen2.5 1.5B（继承其偏见和误差）。仅供研究和开发，不建议直接用于商业。

## 关联

- [[entities/VibeVoice]]
- [[entities/Microsoft]]
- [[concepts/下一令牌扩散]]
- [[concepts/长音频单遍处理]]

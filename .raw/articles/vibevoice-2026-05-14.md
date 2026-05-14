---
source_type: github-repo
url: https://github.com/microsoft/VibeVoice
repo: microsoft/VibeVoice
stars: 47087
language: Python
license: MIT
fetched_at: 2026-05-14
---

# VibeVoice: Open-Source Frontier Voice AI

Microsoft Research, GitHub, ⭐ 47,087, Python, MIT

## Overview

VibeVoice is a family of open-source frontier voice AI models including TTS and ASR.

Core innovation: continuous speech tokenizers (Acoustic and Semantic) at ultra-low frame rate of **7.5 Hz**, preserving audio fidelity while boosting computational efficiency. Uses a **next-token diffusion** framework: LLM understands textual context, diffusion head generates high-fidelity acoustic details.

## Models

### VibeVoice-ASR-7B (2026-01-21)
- 60-minute long-form audio in a single pass (64K token context)
- Structured output: Who (Speaker) + When (Timestamps) + What (Content)
- 50+ languages
- Customized Hotwords support
- vLLM inference supported
- Available on HuggingFace Transformers (2026-03-06)
- arXiv: https://arxiv.org/pdf/2601.18184

### VibeVoice-TTS-1.5B (2025-08-25, ICLR 2026 Oral)
- 90-minute long-form multi-speaker TTS
- Up to 4 distinct speakers in a single conversation
- English, Chinese, cross-lingual
- Expressive speech with conversational dynamics
- NOTE: TTS code removed from repo (2025-09-05) after misuse for deepfakes
- Still available on HuggingFace but web UI disabled

### VibeVoice-Realtime-0.5B (2025-12-03)
- Real-time streaming TTS
- ~300ms first audible latency
- Streaming text input
- ~10 minutes robust long-form generation
- Multilingual: DE, FR, IT, JP, KR, NL, PL, PT, ES + 11 English style voices

## Key Technical Innovation

**Next-Token Diffusion**: LLM (Qwen2.5 base) predicts next token for context/flow, diffusion head generates acoustic details. This hybrid LLM+diffusion approach achieves long-form coherence + high fidelity.

**7.5 Hz Frame Rate**: Ultra-low frame rate tokenization (vs typical 50+ Hz) reduces sequence length dramatically, enabling 60-90 minute single-pass processing.

## Risks & Ethics

TTS code removed after deepfake misuse. High-quality synthetic speech risk: impersonation, fraud, disinformation. Research/development only, not recommended for commercial deployment without further testing.

## Links

- Project Page: https://microsoft.github.io/VibeVoice
- HuggingFace: https://huggingface.co/collections/microsoft/vibevoice-68a2ef24a875c44be47b034f
- ASR Playground: https://aka.ms/vibevoice-asr

# Effective Context Engineering for AI Agents

Source: https://www.anthropic.com/engineering/effective-context-engineering-for-ai-agents
Fetched: 2026-05-26

---

## Core Concept

Context engineering represents an evolution beyond prompt engineering, focusing on optimizing the entire set of tokens available to language models during inference. It involves "curating and maintaining the optimal set of tokens (information) during LLM inference."

## Key Definitions

**Context Engineering vs. Prompt Engineering:**
- Prompt engineering: writing and organizing LLM instructions for optimal outcomes
- Context engineering: managing all information — system instructions, tools, external data, and message history — across multiple inference turns

## Why It Matters

LLMs experience "context rot," where performance degrades as token count increases. This occurs due to architectural constraints in transformer models, where attention relationships scale quadratically with sequence length (n² relationships for n tokens).

## Core Principles

**High-Signal Token Curation:**
The guiding principle is finding "the smallest possible set of high-signal tokens that maximize the likelihood of some desired outcome."

**System Prompts Should Achieve "Right Altitude":**
Instructions must balance specificity with flexibility, avoiding both brittle hardcoded logic and vague guidance that assumes shared context.

**Tool Design Matters:**
Tools should be "self-contained, robust to error, and extremely clear with respect to their intended use." Bloated tool sets with overlapping functionality create ambiguity.

## Advanced Techniques for Long-Horizon Tasks

**1. Compaction**
Summarizing conversation history and reinitializing new context windows with condensed information, preserving critical architectural decisions while discarding redundant outputs.

**2. Structured Note-Taking**
Agents maintain persistent memory outside the context window, enabling tracking across complex tasks. "Allows the agent to track progress across complex tasks, maintaining critical context."

**3. Sub-Agent Architectures**
Specialized agents handle focused tasks with clean context windows, returning condensed summaries to a coordinating agent, achieving "clear separation of concerns."

## Runtime Context Retrieval

Modern agents increasingly use "just in time" context strategies, maintaining lightweight identifiers and dynamically loading data via tools rather than pre-processing everything upfront. This mirrors human cognition and enables "progressive disclosure."

## Hybrid Approaches

The most effective solutions often combine strategies — retrieving some data upfront for speed while allowing autonomous exploration when beneficial, depending on task characteristics.

## Practical Guidance

- Start with minimal prompts using the most capable models
- Add instructions based on failure modes
- Treat context as a "precious, finite resource" regardless of model improvements

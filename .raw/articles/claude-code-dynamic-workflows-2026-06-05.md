---
source_url: https://claude.com/blog/a-harness-for-every-task-dynamic-workflows-in-claude-code
fetched: 2026-06-05
published: 2026-06-02
authors:
  - Thariq Shihipar
  - Sid Bidasaria
title: "A harness for every task: dynamic workflows in Claude Code"
category: Claude Code
---

# A harness for every task: dynamic workflows in Claude Code

Authors: Thariq Shihipar and Sid Bidasaria, members of technical staff at Anthropic working on Claude Code.

Date: June 2, 2026

## Overview

Claude Code can now write and orchestrate its own multi-agent harness dynamically. The article explains how these dynamic workflows function and which patterns yield the best results.

The core premise: "Claude can now write its own harness on the fly, custom-built for the task at hand." While the default Claude Code harness is designed for coding, it works for many other tasks because many tasks structurally resemble coding. But certain task categories have previously required custom harnesses for peak performance — examples cited include Research, security analysis, agent teams, and Code Review.

Workflows allow dynamic creation of harnesses on top of Claude Code, enabling Claude to "solve all of those problems more natively." They can also be shared and reused.

A caveat noted: "best practices are still developing: dynamic workflows often use more tokens and are best suited for complex, high value tasks."

## How Dynamic Workflows Work

Dynamic workflows "execute a javascript file with a few special functions that help spawn and coordinate subagents." Standard JavaScript functions (JSON, Math, Array) are available within workflows to help process data.

Key capability: workflows "can decide which models an agent uses and whether subagents are run in their own worktree, allowing Claude to choose the intelligence level and isolation needed."

If a workflow is interrupted (by user action or terminal quit), "resuming the session will allow the workflow to pick up where it left off."

## Why Dynamic Workflows

The default Claude Code harness requires both planning and execution within a single context window. For many coding tasks this works well, but it can "break down over long-running, massively parallel, highly structured and/or adversarial tasks."

Three failure modes specific to long-running single-context-window work:
- **Agentic laziness:** Claude stops before finishing a complex, multi-part task, declaring the job done after partial progress (e.g., addressing 35 of 50 items in a security review)
- **Self-preferential bias:** Claude's "tendency to prefer its own results or findings, especially when asked to verify or judge them against a rubric"
- **Goal drift:** "gradual loss of fidelity to the original objective across many turns, especially after compaction" — each summarization step is lossy

Workflows combat these by orchestrating "separate Claude subagents with their own context windows and focused, isolated goals."

## Dynamic vs Static Workflows

Static workflows (built with the Claude Agent SDK or `claude -p`) coordinate multiple Claude Code instances. Because they "need to work for all edge cases, they are usually more generic."

With Claude Opus 4.8, dynamic workflows leveraged Claude's intelligence to write custom harnesses tailored to each specific use case.

## Six Patterns

### 1. Classify-and-act
A classifier agent determines the task type, then routes to different agents or behaviors accordingly. A classifier can also determine output type at the end.

### 2. Fan-out-and-synthesize
Split a task into smaller steps, run an agent per step, then synthesize results. Useful when there are a large number of smaller steps or when steps benefit from isolated context windows. The synthesize step acts as a barrier — it waits for all the fan-out agents, then merges their structured outputs into one result.

### 3. Adversarial verification
For each spawned agent, a separate agent adversarially verifies its output against a rubric or criteria.

### 4. Generate-and-filter
Generate multiple ideas on a topic, then filter them by a rubric or by verification, dedupe duplicates and return only the highest quality, tested ideas.

### 5. Tournament
Spawn N agents that each attempt the same task using different approaches. Prompts or models judge results pairwise using a judging agent until a winner emerges.

### 6. Loop until done
For tasks with an unknown amount of work, loop spawning agents until a stop condition is met (no new findings, no more errors in logs) rather than a fixed number of passes.

## Use Cases

- **Migrations and refactors:** Bun was rewritten from Zig to Rust using workflows. Strategy: break task into steps, spin off subagent per fix in worktree, adversarially review each, merge.
- **Deep research:** `/deep-research` skill uses dynamic workflows: fan-out web searches, fetch sources, adversarially verify claims, synthesize cited report.
- **Deep verification:** One agent identifies factual claims, subagents check each in detail, verification agents check source quality.
- **Sorting:** For 1000+ items, use tournament, pipeline of pairwise-comparison agents, or bucket-rank in parallel then merge. "Comparative judgment is more reliable than absolute scoring."
- **Memory and rule adherence:** Create verifier agents — one per rule. Skeptic persona reviews rules to avoid false positives. Reverse: mine sessions for recurring corrections, cluster with parallel agents, adversarially verify, distill into CLAUDE.md.
- **Root-cause investigation:** Generate hypotheses from "disjoint evidence" — separate agents for logs, files, data. Each hypothesis faces a panel of verifiers and refuters.
- **Triaging at scale:** Classifier dedupes against tracked items, fixes or escalates. Quarantine pattern: agents reading untrusted content barred from high-privilege actions.
- **Exploration and taste:** Explore many solutions, review agent evaluates against rubric, done when criteria met.
- **Evals:** Spin off agents in worktree, comparison agents grade outputs against rubric.
- **Model and intelligence routing:** Classifier agent determines which model to use based on task complexity.

## When Not to Use

Workflows "may end up using significantly more tokens." Guiding question: "does it really need more compute?" Most traditional coding tasks "do not need a panel of 5 reviewers."

## Tips

- Detailed prompting with specific techniques creates best results
- Combine with `/loop` and `/goal` for repeatable workflows
- Set token budgets: "use 10k tokens"
- Save by pressing "s" in workflow menu; check into `~/.claude/workflows` or distribute via skill
- For skill distribution: put JS workflow files in skill folder, reference in SKILL.MD
- Prompt Claude to "think of the workflows in the skill as a template instead of a script that needs to be run verbatim"

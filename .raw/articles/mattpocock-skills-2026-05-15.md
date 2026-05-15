---
source_type: github-repo
url: https://github.com/mattpocock/skills
repo: mattpocock/skills
stars: 82759
language: Shell
license: MIT
fetched_at: 2026-05-15
---

# Skills For Real Engineers — mattpocock/skills

Matt Pocock (Total TypeScript), GitHub, ⭐ 82,759, MIT
"Skills for Real Engineers. Straight from my .claude directory."

## Philosophy

Anti-vibe-coding stance. Contrasts with GSD/BMAD/Spec-Kit (own the process, remove control).
These skills: small, composable, hackable, model-agnostic.

## 4 Failure Modes of AI-Assisted Development

### #1: The Agent Didn't Do What I Want → Misalignment
Fix: Grilling session — agent asks you detailed questions before starting
- `/grill-me`: general grilling for any task
- `/grill-with-docs`: same + builds CONTEXT.md + ADRs

### #2: The Agent Is Too Verbose → Jargon Gap
Fix: Shared domain language (CONTEXT.md) — document your project's ubiquitous language
- Before: "a lesson inside a section is made 'real' (given a spot in the file system)"
- After: "materialization cascade"
Benefits: consistent naming, easier navigation, fewer tokens spent thinking

### #3: The Code Doesn't Work → Missing Feedback Loops
Fix: Red-green-refactor TDD loop
- `/tdd`: write failing test first, then fix
- `/diagnose`: disciplined debugging loop (reproduce → minimise → hypothesise → instrument → fix → regression-test)

### #4: We Built A Ball Of Mud → Software Entropy
Fix: Design-first, architecture-aware
- `/to-prd`: quizzes which modules are touched before creating PRD
- `/zoom-out`: explain code in context of the whole system
- `/improve-codebase-architecture`: rescue ball-of-mud codebases, run every few days

## Skills Reference

### Engineering (daily use)
- `/diagnose` — disciplined bug/perf diagnosis loop
- `/grill-with-docs` — grilling + CONTEXT.md + ADR updates
- `/triage` — issue triage state machine
- `/improve-codebase-architecture` — find deepening opportunities informed by CONTEXT.md and ADRs
- `/setup-matt-pocock-skills` — per-repo config (issue tracker, labels, doc layout); run once
- `/tdd` — TDD with red-green-refactor, one vertical slice at a time
- `/to-issues` — break plan/spec/PRD into independently-grabbable GitHub issues
- `/to-prd` — synthesize current conversation into a PRD and GitHub issue
- `/zoom-out` — broader context / higher-level perspective on unfamiliar code
- `/prototype` — throwaway prototype (terminal app for logic OR multiple UI variations on one route)

### Productivity (general workflow)
- `/caveman` — ultra-compressed communication, cuts token usage ~75%
- `/grill-me` — relentless interview about a plan until all decision branches resolved
- `/handoff` — compact conversation into handoff doc for another agent
- `/write-a-skill` — create new skills with proper structure

### Misc
- `/git-guardrails-claude-code` — hooks blocking dangerous git commands
- `/setup-pre-commit` — Husky + lint-staged + Prettier + type check + tests

## Key Insight: CONTEXT.md

Domain ubiquitous language doc for agents. Decodes project jargon.
Benefits: variable/function/file naming consistency, easier codebase navigation, fewer tokens spent thinking.
Built by `/grill-with-docs`. Updated alongside ADRs.

## Installation
```bash
npx skills@latest add mattpocock/skills
```
Then run `/setup-matt-pocock-skills` in your agent.

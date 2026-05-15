---
source_type: youtube-talk
url: https://www.youtube.com/watch?v=v4F1gFy-hqg
title: "Software Fundamentals Matter More Than Ever"
speaker: Matt Pocock
channel: AI Engineer
duration: 18:26
transcript_method: yt-dlp auto-captions
fetched_at: 2026-05-15
---

# Software Fundamentals Matter More Than Ever — Matt Pocock (AI Engineer)

18-minute conference talk. After 18 months teaching AI coding, Matt Pocock observes that devs who succeed aren't those who delegate everything or nothing — they're those who fall back on software engineering fundamentals.

## Core Thesis

"Code is not cheap. In fact, bad code is the most expensive it's ever been."

Specs-to-code movement (GSD/BMAD/Spec-Kit): write a spec, compile to code, if broken update spec and compile again. Matt's experience: each iteration produces worse code. This is "vibe coding by another name."

The insight: AI does really well in GOOD codebases. So good codebases matter more than ever. So software fundamentals matter more than ever.

## Failure Mode #1: AI Didn't Do What I Wanted → Misalignment

Root cause: Design Concept (Frederick P. Brooks, The Design of Design).
When more than one person designs something together, there's an invisible shared idea — the "design concept" — floating between them. You and the AI don't share a design concept.

Fix: `/grill-me` — "Interview me relentlessly about every aspect of this plan until we reach a shared understanding. Walk down each branch of the design tree, resolving dependencies between decisions one by one."

Matt's note: This is better than Claude Code's default Plan mode. Plan mode is eager to create an asset (a plan). Grill Me reaches a shared design concept first.

## Failure Mode #2: AI Too Verbose → Domain Language Gap

Root cause: AI doesn't know your project's terminology. Uses 20 words where 1 would do.

Fix: Ubiquitous Language (DDD concept) → CONTEXT.md
A markdown file full of shared terms. Pass it to the AI. "By reading the thinking traces, it not only improves the planning, but allows the AI to think in a less verbose way."

Skill evolution: started as `/ubiquitous-language` (deprecated), now integrated into `/grill-with-docs`.

## Failure Mode #3: Code Doesn't Work → Feedback Loops

Root cause: LLM "outruns its headlights" (Pragmatic Programmer). Does too much at once, then type-checks after. "The rate of feedback is your speed limit."

Fix: TDD — `/tdd`
Forces LLM to take small steps. Create a failing test → make it pass → refactor.

## Key Structural Insight: Deep Modules vs Shallow Modules (John Ousterhout)

AI is very good at creating shallow-module codebases (many small files, complex interfaces). These are hard for AI to navigate and understand.

Deep modules: lots of functionality hidden behind a simple interface.
Shallow modules: not much functionality, complex interface.

A codebase of deep modules is:
- Easier for AI to navigate (it tests at the interface, not through all the internals)
- Easier for your brain (treat implementation as a gray box)
- More testable (TDD at the boundary)

Fix: `/improve-codebase-architecture` — find opportunities to wrap related code in deep modules.

## Failure Mode: Brain Can't Keep Up

When you ship more than ever, your brain struggles with complexity. Deep modules help: treat non-critical modules as gray boxes. "Design the interface, delegate the implementation."

Kent Beck: "Invest in the design of the system every day."

## The AI = Tactical, You = Strategic

"If we think of AI as a really great on-the-ground programmer — a tactical programmer, a sergeant on the ground making code changes — you need someone above that. Someone thinking on the strategic level. And that's you."

This requires software fundamentals: DDD, TDD, deep modules, design concepts.

## Books Referenced

- A Philosophy of Software Design — John Ousterhout (deep modules)
- The Pragmatic Programmer — David Thomas & Andrew Hunt (software entropy, rate of feedback, outrunning headlights)
- The Design of Design — Frederick P. Brooks (design concept)
- Domain-Driven Design — Eric Evans (ubiquitous language)
- Extreme Programming Explained — Kent Beck ("invest in the design every day")

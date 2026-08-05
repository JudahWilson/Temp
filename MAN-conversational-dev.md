---
inclusion: manual
name: conversational-development
description: A conversational approach for gathering requirements up front rather than starting by making assumptions.
---

# Conversational Development Workflow

A hybrid workflow: conversational requirements gathering up front, then hand off to the structured spec flow (design → tasks → implement) once requirements are solid.

## Phase 1: Conversational Requirements

The goal is to help the user think through their own problem by asking questions — not to suggest solutions or take action prematurely. You are a sounding board, not a decision-maker.

### Principles

- **Ask, don't suggest.** Open-ended questions only. No proposals, no "how about X?", no solutions until the user arrives at one themselves.
- **Never act without a conclusion.** Do not write code, create files, or propose implementations until the user explicitly states what they want built and says to proceed.
- **Follow their thread.** If they're exploring an idea, explore it with them. Don't redirect toward closure.
- **Silence is fine.** If they're thinking, let them think. Don't fill space with suggestions.

### Flow

1. **Mirror** — Restate what you heard in 1-2 sentences to confirm understanding. No additions, no spin.
2. **Ask one open question** — Something that helps them clarify their own thinking. Examples:
   - "What's the actual problem you're running into?"
   - "What would the ideal outcome look like to you?"
   - "What have you already considered?"
   - "Where does this break down?"
   - "What's the constraint that matters most here?"
3. **Wait** — Let them answer. Don't stack questions or preempt their response with options.
4. **Repeat** — Mirror, ask, wait. As many rounds as needed until *they* state a direction.
5. **Converge only when they do** — When the user says something conclusive ("I think I want X", "let's do Y"), then and only then summarize into a requirements shape:
   - What we're building (scope)
   - Key behaviors and constraints
   - How it fits into existing code (touchpoints)
   - Anything explicitly out of scope
6. **Confirm** — "Does this capture it? Anything to add or change?"

### Anti-patterns (do NOT do these)

- Offering 2 options with a recommendation
- Saying "how about we do X?"
- Proposing a mental model before the user has articulated one
- Jumping to code sketches or pseudocode to "clarify approach"
- Moving toward closure before the user signals they're ready
- Adding scope the user didn't mention

## Phase 2: Transition (triggered by "Build It" hook or user confirmation)

When the user approves the requirements (triggers Build It, or says "looks good, let's plan it"):

1. Derive a kebab-case feature name from the conversation
2. Create `.kiro/specs/{feature-name}/requirements.md` using the agreed requirements
3. Present the requirements doc to the user for a final sanity check
4. On approval, proceed to generate the technical design (design.md) — this is where I identify:
   - Files to create or modify
   - Data models / schema changes
   - API contracts
   - Dependencies and integration points
5. Present the design for review

## Phase 3: Task Breakdown

After design approval:

1. Generate `tasks.md` — a chunked, ordered list of implementation steps
2. Each task should be a self-contained unit of work (one logical change)
3. Tasks should be ordered so earlier tasks don't depend on later ones
4. Present the task list for review — user can reorder, split, or remove tasks

## Phase 4: Implementation

Execute tasks one at a time:

1. Announce which task you're starting
2. Implement it
3. Verify (build/test if applicable)
4. Summarize what was done
5. Move to the next task (or pause for user input if the next task has a decision point)

## Guidelines

- If the user gives a clear, complete description with a stated conclusion upfront, skip to confirming the requirements summary — don't add unnecessary question rounds
- Never present options or recommendations during Phase 1 — that's the user's job
- The spec files (requirements.md, design.md, tasks.md) serve as living documentation — they stay in the repo for future reference
- If the feature is small (single file, < 50 lines of change), skip the formal spec and just build it — but only after the user has stated what they want
- Code sketches, approach comparisons, and technical proposals belong in Phase 2 (design), never Phase 1

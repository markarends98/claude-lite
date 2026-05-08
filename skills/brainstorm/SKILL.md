---
name: brainstorm
description: Use only when the user is starting a new feature, new component, or a significant architectural change that requires design decisions before coding. Do NOT use for small changes, isolated bug fixes, refactors of existing code, or anything already in progress.
---

# Brainstorm

Enter plan mode immediately using the `EnterPlanMode` tool before doing anything else. No narration — do not explain what you are about to do at any step.

## Step 1 — Clarify

Ask clarifying questions one at a time. One line per question, no preamble. Once the goal, constraints, and definition of done are clear, move to Step 2.

## Step 2 — Design

Present design in a single response. Bullet points only — no prose paragraphs.

- **What it does** — user-facing behaviour
- **How it works** — key architectural decisions, data flow, interfaces
- **What it touches** — files, modules, dependencies affected

## Step 3 — Approval

Ask: "Does this look right?"

Wait. If the user wants changes, revise Step 2 and ask again. Repeat until approved.

## Step 4 — Plan (automatic)

Invoke the `plan` skill immediately. No confirmation, no restatement of the design. After the plan is output, ask: "Ready to implement?" — then exit plan mode using the `ExitPlanMode` tool.

---
name: brainstorm
description: Use only when the user is starting a new feature, new component, or a significant architectural change that requires design decisions before coding. Do NOT use for small changes, isolated bug fixes, refactors of existing code, or anything already in progress.
---

# Brainstorm

4 steps. No more.

## Step 1 — Clarify (max 3 questions)

Ask clarifying questions one at a time. Hard stop at 3. If the goal still isn't clear after 3 questions, tell the user the task needs to be broken into smaller pieces — do not ask more questions.

Focus on: what problem does this solve, what are the constraints, what does done look like.

## Step 2 — Design

Present functional and technical design in a single response:

- **What it does** — user-facing behaviour
- **How it works** — key architectural decisions, data flow, interfaces
- **What it touches** — files, modules, dependencies affected

No preamble. Keep it tight.

## Step 3 — Approval

Ask: "Does this look right?"

Wait. If the user wants changes, revise step 2 and ask again. Repeat until approved.

## Step 4 — Plan (automatic)

Invoke the `plan` skill. No confirmation, no interaction. After the plan is output, ask: "Ready to implement?"

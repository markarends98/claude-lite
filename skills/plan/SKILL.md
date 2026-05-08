---
name: plan
description: Use after a design has been approved in brainstorm to produce an implementation plan. Do not invoke manually — called automatically from brainstorm step 4.
---

# Plan

Enter plan mode using the `EnterPlanMode` tool if not already in it. Output the plan in one response then exit plan mode using the `ExitPlanMode` tool. No narration, no restatement of the design, no back-and-forth.

## Format

**Complex or critical tasks:**

### Task N: [Name]
**Files:** `path/to/file`
1. What to do
   - Watch out for: [gotcha, if any]
   - Verify: [how to confirm it worked]
   - Perf: [patterns to avoid, if performance-sensitive]

**Simple tasks** — grouped at the end as a checklist:
- [ ] task

## Rules

- Complex tasks first, simple tasks at the end
- No padding — only what the implementer needs
- File paths only, no descriptions of what files are
- Omit Watch out for / Verify / Perf lines if not applicable — never pad
- A long plan means the task needs decomposing

## Implementation cadence

Always end the plan with this line (verbatim):

> **Implement one task at a time.** Complete a task, then wait for confirmation before starting the next.

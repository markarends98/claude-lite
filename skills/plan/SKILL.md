---
name: plan
description: Use after a design has been approved in brainstorm to produce an implementation plan. Do not invoke manually — called automatically from brainstorm step 4.
---

# Plan

Output the implementation plan in one response. No back-and-forth, no confirmation.

## Format

**Complex or critical tasks** — step-by-step with detail:

### Task N: [Name]
**Files:** list files to create or modify
1. [What to do]
   - Watch out for: [gotcha, if any]
   - Verify: [how to confirm it worked]

**Simple tasks** — bullet list only, grouped at the end:

**Simple tasks:**
- [ ] [task]
- [ ] [task]

## Rules

- Complex tasks first, simple tasks at the end
- Only include what the implementer needs — no padding
- No interaction during planning — full plan in one response
- Keep the plan itself lean: a long plan is a sign the task needs decomposing

## Performance requirements (per task)

For every task that involves per-frame code, collections, or hot paths, add a **Perf:** line listing the specific patterns required:

- Allocations: pre-allocate scratch arrays/objects; no `{}`, `[]`, spread, `.map()`, `.filter()` in hot paths
- Loops: `for (let i = 0; i < n; i++)`, cache `array.length`, no `for..of` on arrays
- Map/Set: single `get()` + null check — never `has()` + `get()`; never spread into array
- Removal: swap-remove for O(1) unordered removal; batch removals after iteration
- Property access: cache resolved config values at init; no `?? default` evaluated every frame

If a task has no hot paths, omit the Perf line. Never pad tasks with a Perf line they don't need.

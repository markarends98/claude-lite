---
name: code-review
description: Use after completing an implementation, significant feature, or a meaningful chunk of work to verify correctness before moving on. Do NOT use mid-implementation, for trivial changes, or before the work is actually done.
---

# Code Review

Dispatch a reviewer subagent on Haiku. Code review is pattern matching — Haiku handles it well at lower cost.

## Step 1 — Collect context

```bash
git rev-parse HEAD~1   # BASE_SHA — SHA before the work started
git rev-parse HEAD     # HEAD_SHA — current commit
```

Note what was implemented in one sentence.

## Step 2 — Dispatch subagent

Dispatch an Agent subagent with `model: haiku` and the following prompt (fill in placeholders):

---

Review the git diff from BASE_SHA to HEAD_SHA.

What was implemented: WHAT_WAS_IMPLEMENTED

Check both correctness AND performance. For performance, apply this checklist to any per-frame, hot-path, or collection code:

- Allocations: no `{}`, `[]`, spread `...`, `.map()`, `.filter()` in hot paths — pre-allocate and mutate in place
- Loops: use `for (let i = 0; i < n; i++)`, cache `array.length`, no `for..of` on arrays
- Map/Set: single `get()` + null check — never `has()` + `get()`; never `[...map.values()]` or `[...set]`
- Removal: swap-remove (`arr[i] = arr[last]; arr.pop()`) for O(1) unordered removal; batch removals after iteration
- Property access: cache stable config values at init — no `?? default` or `|| default` evaluated every frame

**Output format — follow exactly:**

**Verdict:** pass | pass with notes | needs work

For each complex or critical finding:
- What is wrong
- Why it matters
- How to fix it

For minor findings: one bullet per issue.

No preamble. No summary. Lead with the verdict.

---

## Step 3 — Act on feedback

- **needs work** — fix critical issues before proceeding
- **pass with notes** — fix minor issues, then continue
- **pass** — continue

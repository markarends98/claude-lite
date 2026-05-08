---
name: code-review
description: Use after completing an implementation, significant feature, or a meaningful chunk of work to verify the code matches the project's coding standards before moving on. Do NOT use mid-implementation, for trivial changes, or before the work is actually done.
---

# Code Review

No narration between steps — just execute.

## Step 1 — Run project tooling

Detect available tools and scripts in one pass:

```bash
ls .prettierrc* prettier.config.* .eslintrc* eslint.config.* biome.json .stylelintrc* tsconfig.json 2>/dev/null
node -e "const s=require('./package.json').scripts||{};console.log(Object.keys(s).filter(k=>/lint|format|check|typecheck/.test(k)).map(k=>k+': '+s[k]).join('\n'))" 2>/dev/null
```

Run every tool found with its auto-fix flag. If a tool has no auto-fix flag, fix errors manually. Fix all type errors from `tsc --noEmit` if applicable.

## Step 2 — Load standards

Read the project's `CLAUDE.md` in full and extract coding standards — naming conventions, architectural patterns, and anything tools cannot catch.

## Step 3 — Review

```bash
git diff HEAD~1 HEAD
```

Check the diff against the standards. Output findings only — no summary of what passed.

**Verdict:** pass | pass with notes | needs work

For each finding:
- What is wrong
- Which rule it violates
- How to fix it

Lead with the verdict. No preamble.

## Step 4 — Act

- **needs work** — fix before proceeding
- **pass with notes** — fix minor issues, then continue
- **pass** — continue

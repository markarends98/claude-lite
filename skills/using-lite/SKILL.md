---
name: using-lite
description: Gatekeeper — evaluate at the start of every user message whether a skill should be invoked. Only invoke when a task clearly matches. Never invoke for questions, explanations, continuing existing work, single-file edits, bug fixes, test runs, or git operations.
---

# using-lite

Evaluate once per message. Three outcomes only:

## 1. Invoke a skill

Only when the task **clearly and obviously** matches:

| Task | Skill |
|------|-------|
| Starting a new feature, component, or significant change | `brainstorm` |
| Just completed an implementation or feature | `code-review` |

No other skills exist in this plugin.

## 2. Remind about Haiku

When the task is lightweight, output this single line before responding — then respond normally. Do not invoke a skill.

> This looks like a Haiku-level task — consider `/model haiku`.

**Lightweight tasks:** answering questions, explaining code, reading files, small isolated edits, single-file changes, bug fixes under 10 lines, running tests, git operations, continuing work already in progress.

## 3. Do nothing

For everything else — just respond. No reminder, no skill.

## Mid-session suppression

Once an implementation plan is being executed (tasks are being worked through), suppress brainstorm and plan. Only code-review remains eligible after a task or the full plan is complete.

## Do-not-trigger list

Never invoke any skill for:
- Answering a question
- Explaining or reading code
- Continuing work already underway
- Single-file changes
- Small bug fixes
- Running tests
- Git operations (commit, push, status, log)
- Anything completable in under 5 minutes

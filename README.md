# claude-lite

Lightweight Claude Code plugin with opinionated skills for feature development and code review.

## Skills

- **brainstorm** — clarify, design, and plan a feature before writing any code
- **plan** — produce a lean, step-by-step implementation plan (called automatically from brainstorm)
- **code-review** — run project tooling, fix errors, and verify the diff against your project's coding standards

## Global behaviour

When installed, the plugin applies these rules to every conversation:

- Direct responses, no filler or small talk
- Challenges flawed assumptions instead of defaulting to agreement
- Matches explanation depth to the topic — simple answers for simple questions
- Asks one clarifying question when intent is ambiguous, states assumptions and proceeds when confident

## Install

```
/plugin marketplace add markarends98/claude-lite
/plugin install claude-lite@markarends98-claude-lite
```

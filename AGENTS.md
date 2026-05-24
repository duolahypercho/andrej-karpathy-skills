# AGENTS.md

This repository is a Codex-first skill package.

## Codex Entry Points

- Plugin manifest: `.codex-plugin/plugin.json`
- Skill instructions: `skills/karpathy-guidelines/SKILL.md`
- Examples: `EXAMPLES.md`

## Agent Behavior

Use the Karpathy guidelines whenever writing, reviewing, or refactoring code:

- Think before coding: surface assumptions, confusion, alternatives, and tradeoffs before implementation.
- Simplicity first: use the minimum code that solves the requested problem.
- Surgical changes: touch only what the task requires and clean up only changes introduced by the task.
- Goal-driven execution: define success criteria and verify the work against them when appropriate.

## Repository Rules

- Keep this repo Codex-native.
- Do not add instruction files or plugin metadata for other agent runtimes.
- Keep `SKILL.md` as the source of truth for reusable skill behavior.
- Keep `README.md` focused on Codex installation and usage.

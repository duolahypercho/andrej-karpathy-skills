# Surgical Coding Discipline for Codex

A Codex-native skill package for keeping coding agents deliberate, small-scoped, and verification-oriented.

- `AGENTS.md` is the repository-level operating context.
- `.codex-plugin/plugin.json` is the plugin manifest.
- `skills/surgical-coding-discipline/SKILL.md` is the reusable skill.
- `EXAMPLES.md` shows original Codex-style scenarios.

English | [Simplified Chinese](./README.zh.md)

## Why This Exists

Coding agents are strongest when the goal is concrete and the edit surface is narrow. They get expensive when they silently choose an interpretation, expand the task, add abstractions too early, or rewrite code they did not need to touch.

This skill gives Codex a compact operating discipline for that moment.

## The Four Habits

| Habit | What It Prevents |
|-------|------------------|
| State the frame | Silent assumptions and hidden confusion |
| Bias to the smallest useful patch | Premature architecture and option-heavy APIs |
| Touch only the task surface | Drive-by refactors and style churn |
| Prove the outcome | "Looks right" changes without a success check |

## Install In Codex

Use this repository as a local Codex plugin source.

1. Add the repository to your Codex plugin sources.
2. Codex reads `.codex-plugin/plugin.json`.
3. Codex loads `skills/surgical-coding-discipline/SKILL.md`.

Plugin name:

```text
andrej-karpathy-skills
```

Skill name:

```text
surgical-coding-discipline
```

## Repository Layout

```text
.codex-plugin/plugin.json
AGENTS.md
EXAMPLES.md
LICENSE
README.md
README.zh.md
skills/surgical-coding-discipline/SKILL.md
```

## When To Use It

Use the skill when Codex is asked to:

- write new code,
- fix a bug,
- refactor a module,
- review a patch,
- reduce implementation complexity,
- define success criteria before making a risky change.

For tiny edits, Codex should use judgment. The point is not ceremony; the point is avoiding costly, avoidable mistakes.

## Attribution

This package is inspired by Andrej Karpathy's public comments on LLM coding behavior and by earlier community attempts to turn those comments into reusable agent guidance. This repository is a Codex-native rewrite with its own package structure, docs, examples, and operating language.

## License

MIT

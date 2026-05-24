# Karpathy-Inspired Codex Skill

Behavioral guidelines for Codex coding agents, derived from Andrej Karpathy's observations on common LLM coding pitfalls.

This repository is Codex-native. It uses:

- `.codex-plugin/plugin.json` for the Codex plugin manifest.
- `AGENTS.md` for repository-level Codex operating context.
- `skills/karpathy-guidelines/SKILL.md` for reusable skill instructions.
- `EXAMPLES.md` for practical examples of the four principles.

English | [Simplified Chinese](./README.zh.md)

## The Problem

LLM coding agents often make three expensive mistakes:

- They assume too much and hide uncertainty.
- They overcomplicate simple tasks.
- They change unrelated code while trying to help.

## The Skill

The `karpathy-guidelines` skill teaches four operating principles:

| Principle | Purpose |
|-----------|---------|
| Think Before Coding | Surface assumptions, confusion, alternatives, and tradeoffs. |
| Simplicity First | Solve the requested problem with the minimum necessary code. |
| Surgical Changes | Touch only the lines and files required by the task. |
| Goal-Driven Execution | Convert vague requests into verifiable success criteria. |

## Install In Codex

Use this repository as a local Codex plugin source.

1. Add this repository to your Codex plugin sources.
2. Codex reads `.codex-plugin/plugin.json`.
3. Codex loads the skill from `skills/karpathy-guidelines/SKILL.md`.

Plugin name:

```text
andrej-karpathy-skills
```

Skill name:

```text
karpathy-guidelines
```

## Repository Layout

```text
.codex-plugin/plugin.json
AGENTS.md
EXAMPLES.md
README.md
README.zh.md
skills/karpathy-guidelines/SKILL.md
```

## When To Use

Use this skill when Codex is writing, reviewing, or refactoring code and the task benefits from:

- fewer hidden assumptions,
- less overengineering,
- smaller diffs,
- clearer success criteria.

## License

MIT

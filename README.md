# Andrej Karpathy Skill for Codex

A Codex-native packaging of Andrej Karpathy-inspired coding-agent guidelines.

- `AGENTS.md` is the repository-level operating context.
- `.codex-plugin/plugin.json` is the plugin manifest.
- `skills/andrej-karpathy-skill/SKILL.md` is the reusable skill.
- `instruction.md` is the copy-paste version for Codex Custom Instructions.
- `EXAMPLES.md` shows Codex-style examples.

English | [Simplified Chinese](./README.zh.md)

## Why This Exists

Coding agents often fail in predictable ways:

- they assume too much,
- they overbuild simple requests,
- they edit unrelated code,
- they call work done without a clear success check.

This package turns the original Karpathy-style guidelines into a Codex-ready skill, repo instruction file, and Custom Instructions block.

## The Four Guidelines

| Guideline | Codex Behavior |
|-----------|----------------|
| Think before coding | Surface assumptions, confusion, alternatives, and tradeoffs. |
| Keep it simple | Solve the current request without speculative features or abstractions. |
| Make surgical changes | Touch only what the task requires and preserve surrounding code. |
| Define and verify the goal | Turn the request into a checkable outcome before calling it done. |

## Install In Codex

Use this repository as a local Codex plugin source.

1. Add the repository to your Codex plugin sources.
2. Codex reads `.codex-plugin/plugin.json`.
3. Codex loads `skills/andrej-karpathy-skill/SKILL.md`.

Plugin name:

```text
andrej-karpathy-skills
```

Skill name:

```text
andrej-karpathy-skill
```

## Use Without Installing

If someone does not want to install the plugin or add an `AGENTS.md`, they can use the standalone Custom Instructions version:

1. Open `instruction.md`.
2. Copy the block under "Paste the block below".
3. Paste it into Codex Settings -> Custom Instructions.

That version is self-contained, so Codex can apply the same behavior without reading any repo files.

## Repository Layout

```text
.codex-plugin/plugin.json
AGENTS.md
EXAMPLES.md
instruction.md
LICENSE
README.md
README.zh.md
skills/andrej-karpathy-skill/SKILL.md
```

## Attribution

Inspired by Andrej Karpathy's public comments on LLM coding behavior and by the original community repo that packaged those ideas as reusable agent guidance.

Original repo credit:

```text
multica-ai/andrej-karpathy-skills
```

## License

MIT

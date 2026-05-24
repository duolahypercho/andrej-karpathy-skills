# AGENTS.md

This repository is a Codex-native plugin package. Treat it as a reusable skill, not as a generic prompt dump.

## Source Of Truth

- Plugin manifest: `.codex-plugin/plugin.json`
- Skill behavior: `skills/andrej-karpathy-skill/SKILL.md`
- Custom Instructions copy-paste version: `instruction.md`
- Usage examples: `EXAMPLES.md`
- Public overview: `README.md`

## Package Intent

The package teaches Codex the four Karpathy-inspired coding-agent checks:

- think before coding,
- keep implementations simple,
- make surgical changes,
- define the goal and verify it.

## Maintenance Rules

- Keep this repository Codex-native.
- Do not add instruction files or plugin metadata for other agent runtimes.
- Keep `SKILL.md` as the behavioral source of truth.
- Keep `instruction.md` self-contained so it works without `AGENTS.md`.
- Keep examples concrete and code-adjacent, not motivational.
- Keep attribution in `README.md`, but do not copy upstream wording wholesale.
- Avoid non-ASCII symbols in English docs unless the file already requires them.

## Quality Bar

Before publishing a change, confirm:

- The file list still matches the Codex package shape.
- The manifest points to this repository.
- README, AGENTS, and SKILL describe the same behavior.
- `instruction.md` matches the same workflow and can be pasted into Custom Instructions.
- Examples use clean plain text and do not depend on another runtime.

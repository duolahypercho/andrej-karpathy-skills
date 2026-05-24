# AGENTS.md

This repository is a Codex-native plugin package. Treat it as a reusable skill, not as a generic prompt dump.

## Source Of Truth

- Plugin manifest: `.codex-plugin/plugin.json`
- Skill behavior: `skills/change-budget/SKILL.md`
- Usage examples: `EXAMPLES.md`
- Public overview: `README.md`

## Package Intent

The package teaches Codex a change-budget workflow:

- define `Outcome`, `Boundary`, `Non-goals`, `Risk`, and `Evidence`,
- choose the right mode for implementation, debugging, refactoring, or review,
- separate core work from optional expansion,
- report only the evidence actually gathered.

## Maintenance Rules

- Keep this repository Codex-native.
- Do not add instruction files or plugin metadata for other agent runtimes.
- Keep `SKILL.md` as the behavioral source of truth.
- Keep examples concrete and code-adjacent, not motivational.
- Keep attribution in `README.md`, but do not copy upstream wording wholesale.
- Avoid non-ASCII symbols in English docs unless the file already requires them.

## Quality Bar

Before publishing a change, confirm:

- The file list still matches the Codex package shape.
- The manifest points to this repository.
- README, AGENTS, and SKILL describe the same behavior.
- Examples use clean plain text and do not depend on another runtime.

# Using this repo with Codex and Cursor

This repository is now organized as a Codex plugin-first package.

- Primary: `.codex-plugin/plugin.json`
- Primary instructions: `skills/karpathy-guidelines/SKILL.md`
- Optional compatibility: `CLAUDE.md`, `.cursor/rules/karpathy-guidelines.mdc`

## Codex (primary)

Use this repo directly as a Codex plugin source.

1. Add the repo folder to your Codex plugin source path.
2. Let Codex discover `.codex-plugin/plugin.json`.
3. The skill name is `andrej-karpathy-skills` and the skill entry is `karpathy-guidelines`.

## Cursor (optional)

1. Open the folder in Cursor.
2. The committed project rule `/.cursor/rules/karpathy-guidelines.mdc` is available with `alwaysApply: true`.
3. In Cursor settings, confirm `karpathy-guidelines` appears under project rules.

## Other tools

- If a stack only supports a root instruction file, keep this guidance in `CLAUDE.md`.
- If you copy rules elsewhere, keep `SKILL.md` as the source-of-truth for the four principles.

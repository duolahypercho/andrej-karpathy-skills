---
name: andrej-karpathy-skill
description: Apply Andrej Karpathy-inspired coding-agent guidelines in Codex. Use when writing, reviewing, debugging, or refactoring code to surface assumptions, avoid overengineering, keep edits surgical, and define verifiable success criteria.
---

# Andrej Karpathy Skill

Use this skill as a Codex-native version of the Karpathy coding-agent guidelines.

The goal is not to add a new framework. The goal is to make Codex behave more carefully on real code: clarify before guessing, prefer simple implementations, avoid unrelated edits, and verify against a concrete goal.

## The Four Checks

### 1. Think Before Coding

Before editing, make the task explicit.

- State the interpretation you are using.
- Surface assumptions that affect the implementation.
- Name meaningful tradeoffs when more than one path is reasonable.
- Ask a concise clarifying question when guessing would create real risk.
- If the task is obvious and low-risk, state the assumption briefly and proceed.

Codex should not silently pick a risky interpretation and run with it.

### 2. Keep It Simple

Implement the smallest thing that satisfies the current request.

- Do not add features the user did not ask for.
- Do not add configurability before there is a real need.
- Do not create abstractions for one caller.
- Do not introduce new dependencies for logic the repo can already express simply.
- If the first approach feels like architecture, look for the direct version first.

Codex should solve today's problem, not design tomorrow's system by accident.

### 3. Make Surgical Changes

Keep the diff tied to the request.

- Touch only the files needed for the task.
- Match the local style even when another style is personally preferable.
- Do not reformat, rename, or reorganize adjacent code as a side effect.
- Clean up imports, variables, or helpers made unused by your own change.
- Mention unrelated dead code or design problems separately instead of fixing them inside the patch.

Codex should leave the surrounding code recognizable.

### 4. Define The Goal And Verify It

Turn the request into a checkable outcome before calling it done.

- Bug fix: identify the failing case and the expected behavior.
- Feature: identify the behavior the user should be able to observe.
- Refactor: identify the behavior that must remain unchanged.
- Review: identify concrete risks, missing tests, and regressions.

Use the narrowest meaningful verification available. If you do not run a check, say so plainly and explain why.

## Codex Response Pattern

For non-trivial coding work, keep the user oriented with:

```text
Assumption:
Changed:
Verified:
Remaining risk:
```

Use this shape lightly. Do not add ceremony to obvious one-line edits.

## Pushback

Push back gently when the request or your first design would cause avoidable scope growth:

- a broad rewrite for a narrow bug,
- a new abstraction with one use case,
- a formatting sweep mixed into behavior changes,
- a public API expansion that is not required,
- a verification plan too weak for a risky change.

When pushing back, offer the smaller path that still satisfies the user's goal.

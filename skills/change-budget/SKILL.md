---
name: change-budget
description: Apply a Codex-specific change-budget workflow for implementation, debugging, refactoring, and review tasks. Use when Codex should translate a user request into scoped code changes, preserve local contracts, avoid speculative expansion, and report evidence for what changed.
---

# Change Budget

Treat every coding task as a controlled change with a budget, a boundary, and evidence.

This skill is not a style guide. It is a decision protocol for keeping Codex from turning a narrow request into a wandering rewrite.

## The Change Budget

Before editing, establish a small working ledger:

```text
Outcome:
Boundary:
Non-goals:
Risk:
Evidence:
```

Use it lightly. For small tasks, keep it in your head. For risky or multi-file tasks, say the ledger out loud before changing code.

- `Outcome`: the user-visible behavior or code property that must become true.
- `Boundary`: the files, modules, APIs, or ownership areas likely involved.
- `Non-goals`: tempting cleanup that should stay out of the patch.
- `Risk`: what could break if the assumption is wrong.
- `Evidence`: the narrowest command, test, inspection, or artifact that proves the outcome.

If any ledger line is unknown and guessing would create real risk, ask. If the risk is low, proceed and state the assumption.

## Modes

Choose the mode that matches the task. Do not use the same behavior for every request.

### Implementation Mode

Use when adding behavior.

- Start from the call site or user path before adding helpers.
- Fit the smallest current requirement before designing the next one.
- Prefer local code over new shared abstractions until at least two real callers exist.
- Add public API only when the user request needs a public contract.

Done means the requested behavior exists and the evidence path can show it.

### Debugging Mode

Use when fixing a reported failure.

- Name the failure shape first: input, observed result, expected result.
- Change the code nearest to the failing contract.
- Avoid broad rewrites unless the bug is caused by a broad design assumption.
- Preserve unrelated behavior even if it looks imperfect.

Done means the failing shape is addressed and the fix does not rely on accidental behavior.

### Refactor Mode

Use when changing structure without changing behavior.

- Identify the preserved contract before moving code.
- Move in the smallest reversible step.
- Keep names and layout recognizable unless clarity requires otherwise.
- Do not mix refactor work with feature work unless the feature cannot land safely without it.

Done means behavior is preserved and the structure is easier to maintain for the requested reason.

### Review Mode

Use when evaluating code.

- Lead with correctness, regression, security, data-loss, and maintenance risks.
- Tie each finding to a concrete line, behavior, or missing check.
- Avoid preference-only feedback unless the user asks for style review.
- Say when no actionable issues were found.

Done means the user can decide what to fix without reading your mind.

## Expansion Controls

Stop and reconsider when you are about to:

- create a framework for one use case,
- add options the user did not request,
- edit files outside the stated boundary,
- rename things just because they read better,
- change formatting in untouched code,
- replace a working pattern with a preferred pattern,
- make verification broader than the change requires.

When expansion seems useful, split it from the requested patch:

```text
Core change:
Optional follow-up:
Why separate:
```

## Evidence Ledger

At the end, report evidence in proportion to risk.

Use one of these evidence types:

- `Tested`: command or scenario was run.
- `Inspected`: code path or artifact was checked directly.
- `Not run`: verification was skipped, with the reason.
- `Blocked`: verification requires missing access, dependency, data, or user decision.

Do not imply stronger evidence than you have. A passing formatter is not proof that a bug is fixed. A successful build is not proof that the user workflow works.

## Communication Contract

Be concise, but make the state of the work legible.

For ordinary code edits, answer with:

```text
Changed:
Evidence:
Risk:
```

For review tasks, answer with:

```text
Findings:
Open questions:
Residual risk:
```

For blocked tasks, answer with:

```text
Blocked by:
What is already done:
Exact next input needed:
```

The user should be able to see what changed, why it stayed bounded, and what proof exists without digging through the diff.

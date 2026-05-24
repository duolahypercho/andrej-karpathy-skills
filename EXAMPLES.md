# Examples

These examples show how the `andrej-karpathy-skill` should change Codex behavior.

## Example 1: Implementation Mode

User request:

```text
Add CSV export to the customer table.
```

Better Codex ledger:

```text
Outcome: customers visible in the current table can be exported as CSV.
Boundary: customer table component, existing table data shape, one export button.
Non-goals: background jobs, all-customer export, new permission model.
Risk: exporting fields not already visible in the UI.
Evidence: inspect generated CSV columns and run the table component test if present.
```

Patch behavior:

- Use the existing table data rather than querying a second source.
- Export only displayed columns unless the user asks for more.
- Keep styling and pagination changes out of the patch.

## Example 2: Debugging Mode

User request:

```text
The upload endpoint fails when filenames contain spaces.
```

Better Codex ledger:

```text
Outcome: filenames with spaces upload successfully.
Boundary: upload request construction and filename handling.
Non-goals: storage backend rewrite, retry policy, timeout cleanup.
Risk: changing how existing filenames are encoded.
Evidence: add or run a focused filename-with-space case.
```

Patch behavior:

- Reproduce or describe the failing filename shape.
- Fix the code closest to filename encoding.
- Avoid rewriting request handling unless encoding is spread across the boundary.

## Example 3: Refactor Mode

User request:

```text
Make this invoice calculation easier to read.
```

Better Codex ledger:

```text
Outcome: invoice calculation is easier to follow without behavior changes.
Boundary: invoice calculation function and local helpers.
Non-goals: tax rules, rounding policy, database schema.
Risk: changing money behavior while renaming code.
Evidence: existing invoice tests or before/after calculation spot checks.
```

Patch behavior:

- Extract only local concepts already present in the function.
- Preserve rounding order and return shape.
- Do not introduce a pricing abstraction unless multiple callers already need it.

## Example 4: Review Mode

User request:

```text
Review this auth patch.
```

Better Codex ledger:

```text
Outcome: identify correctness and security risks in the patch.
Boundary: changed auth files and their immediate contracts.
Non-goals: style preferences, unrelated auth cleanup.
Risk: missing session invalidation or privilege regression.
Evidence: file/line findings plus tests that should cover each risk.
```

Review behavior:

- Lead with actionable findings.
- Tie each finding to a concrete behavior.
- Separate missing tests from proven bugs.
- Say clearly when no issues are found.

## Mini Template

Use this when a task starts to sprawl:

```text
Core change:
Out of scope:
Evidence I can collect:
Evidence I cannot collect:
```

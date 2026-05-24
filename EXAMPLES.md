# Examples

These examples show how `andrej-karpathy-skill` applies the four guidelines in Codex.

## 1. Think Before Coding

User request:

```text
Add export support for customer records.
```

Better Codex response:

```text
I can add this. I will assume the first version should export the currently visible customer table as CSV, using only fields already shown in the UI. If you meant all customers, background export, or sensitive admin-only fields, that changes the implementation.
```

Why this works:

- It states the interpretation.
- It surfaces risky assumptions.
- It gives the user a chance to correct scope before code changes.

## 2. Keep It Simple

User request:

```text
Add a helper to calculate percentage discounts.
```

Too much:

```python
class DiscountStrategy:
    def apply(self, subtotal):
        raise NotImplementedError


class PercentageDiscount(DiscountStrategy):
    def __init__(self, rate):
        self.rate = rate

    def apply(self, subtotal):
        return subtotal * self.rate
```

Better:

```python
def calculate_discount(subtotal, rate):
    return subtotal * rate
```

Why this works:

- The request asked for a helper, not a pricing framework.
- No abstraction exists before a second real use case appears.
- The simple version is easier to replace later.

## 3. Make Surgical Changes

User request:

```text
Fix upload failures when filenames contain spaces.
```

Better patch behavior:

- Change filename handling only.
- Keep return semantics unchanged.
- Avoid unrelated timeout, type-hint, formatting, or request-client changes.
- Mention separate cleanup opportunities after the fix instead of mixing them into the patch.

Why this works:

- The diff stays tied to the bug.
- Reviewers can see exactly why each changed line exists.
- The patch avoids accidental regressions from unrelated cleanup.

## 4. Define And Verify The Goal

User request:

```text
Sorting breaks when two tasks have the same priority.
```

Better Codex response:

```text
The success criterion is deterministic ordering when priorities match. I will add or inspect a duplicate-priority case, then make the tie-breaker explicit.
```

Better implementation shape:

```python
def sort_tasks(tasks):
    return sorted(tasks, key=lambda task: (task.priority, task.created_at))
```

Why this works:

- The bug becomes a checkable behavior.
- The tie-breaker is explicit.
- Verification is connected to the reported failure.

## Quick Check

Before accepting a patch, ask:

- Did Codex surface assumptions before risky edits?
- Did it solve only the current request?
- Did it avoid unrelated files and formatting churn?
- Did it define what would prove the task is done?

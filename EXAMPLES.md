# Examples

These examples show the expected Codex behavior when the `surgical-coding-discipline` skill is active.

## 1. Frame The Request

User request:

```text
Add export support for customer records.
```

Weak response:

```text
I'll add CSV and JSON export, a scheduled background job, a new admin page,
and a permission model for all customer fields.
```

Better Codex response:

```text
I can add this, but "export support" has a few product choices baked in.
I'll assume you want an authenticated endpoint that exports the currently
filtered customer list as CSV, using only fields already visible in the UI.
If that is wrong, the risky parts are scope, sensitive fields, and file size.
```

Why this is better:

- It names assumptions before code appears.
- It narrows the first implementation.
- It highlights the places where guessing could cause harm.

## 2. Shrink The Patch

User request:

```text
Add a discount calculation helper.
```

Weak implementation:

```python
class DiscountStrategy:
    def apply(self, subtotal):
        raise NotImplementedError


class PercentageDiscount(DiscountStrategy):
    def __init__(self, rate):
        self.rate = rate

    def apply(self, subtotal):
        return subtotal * self.rate


class DiscountEngine:
    def __init__(self, strategy):
        self.strategy = strategy

    def calculate(self, subtotal):
        return self.strategy.apply(subtotal)
```

Better implementation:

```python
def calculate_discount(subtotal, rate):
    return subtotal * rate
```

Why this is better:

- The request asked for a helper, not a pricing framework.
- The simple version is easier to test and replace later.
- No abstraction exists before a second real use case appears.

## 3. Respect The Existing Surface

User request:

```text
Fix upload failures when the filename contains spaces.
```

Weak patch:

```diff
- def upload(path):
-     response = requests.post(URL, files={'file': open(path, 'rb')})
-     return response.status_code == 200
+ def upload(path: str) -> bool:
+     """Upload a file to the remote API."""
+     with open(path, "rb") as handle:
+         response = requests.post(
+             URL,
+             files={"file": (Path(path).name.replace(" ", "_"), handle)},
+             timeout=30,
+         )
+     return response.ok
```

Better patch:

```diff
  def upload(path):
-     response = requests.post(URL, files={'file': open(path, 'rb')})
+     filename = os.path.basename(path)
+     response = requests.post(URL, files={'file': (filename, open(path, 'rb'))})
      return response.status_code == 200
```

Why this is better:

- It fixes the filename behavior without changing style, return semantics, or timeout policy.
- It leaves type hints and resource-management cleanup for a separate request.
- The diff maps directly to the reported bug.

## 4. Prove The Outcome

User request:

```text
Sorting breaks when two tasks have the same priority.
```

Weak response:

```text
I changed the sort function to use priority and title. It should work now.
```

Better Codex flow:

```text
Success criterion: two tasks with the same priority keep deterministic order.

Check:
- Add or identify a case with duplicate priorities.
- Sort by priority first and created time second.
- Run the focused task-sort test.
```

Better patch shape:

```python
def sort_tasks(tasks):
    return sorted(tasks, key=lambda task: (task.priority, task.created_at))
```

Why this is better:

- The bug is translated into a concrete behavior.
- The tie-breaker is explicit.
- Verification is tied to the actual failure mode.

## Quick Diagnostic

Before accepting a patch, ask:

- Did Codex state the frame of the request?
- Is the implementation smaller than the problem?
- Are unrelated files untouched?
- Is there a meaningful success check?

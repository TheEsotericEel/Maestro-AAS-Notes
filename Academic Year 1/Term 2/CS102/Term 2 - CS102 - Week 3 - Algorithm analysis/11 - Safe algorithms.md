# Safe Algorithms: Handling Edge Cases and Bad Input

## 1. Lesson Focus
Writing algorithms that handle unexpected inputs gracefully using defensive programming patterns and guard clauses.

## 2. Core Concepts
**Edge Case**: Input that is possible but not part of the usual "happy" flow—can still crash algorithms if not handled.

**Guard Clause**: An early return or check at the top of a function that prevents dangerous operations from running on invalid input.

**Defensive Programming**: Assuming input might be invalid unless proven otherwise, and adding checks to prevent crashes.

## 3. Edge-Case Checklist
Always ask these questions for any algorithm:
- **Empty**: list/string has length 0
- **One**: exactly 1 item
- **Many**: normal case, multiple items
- **Extremes**: very big/very small numbers, max/min values
- **Null/None**: missing value instead of a list/number/string
- **Wrong type**: string where you expected a number, etc.

## 4. Reliability Pattern
Standard guard clause order:
```python
def function_name(data):
    if data is None:
        # handle None case
        return default_value
    if not isinstance(data, expected_type):
        # handle wrong type
        return default_value
    if not data:
        # handle empty case
        return default_value
    # happy path
```

## 5. Examples

### Example 1: Serving First Order
```python
def serve_first_order(orders):
    if orders is None:
        print("No orders list provided.")
        return
    if not isinstance(orders, list):
        print("Invalid orders data.")
        return
    if not orders:
        print("No orders to serve.")
        return
    first = orders[0]
    print("Serving:", first)
```

**Behavior:**
- `[]` → "No orders to serve."
- `["Mango"]` → "Serving: Mango"
- `None` → "No orders list provided."
- `"not a list"` → "Invalid orders data."

### Example 2: Total Orders Length
```python
def total_orders_length(orders):
    if orders is None:
        print("No orders to measure.")
        return 0
    if not isinstance(orders, list):
        print("Invalid orders list.")
        return 0
    total = 0
    for order in orders:
        total += len(order)
    return total
```

### Example 3: Average Score
```python
def average_score(scores):
    if scores is None:
        print("No scores provided.")
        return None
    if not isinstance(scores, list):
        print("Invalid scores data.")
        return None
    if not scores:
        print("No scores to average.")
        return 0
    total = 0
    for s in scores:
        total += s
    return total / len(scores)
```

## 6. Common Mistakes / What Not to Do
- **Assuming lists are never empty**: Always add `if not data:` guard unless you have enforced non-emptiness elsewhere.
- **Treating None like empty list**: `if not orders:` is True for both `[]` and `None`—use `if orders is None:` to distinguish.
- **Forgetting type checks**: Strings are iterable but may not behave like lists in your algorithm.
- **Skipping guard clauses**: "The code above guarantees this" is fragile—defensive checks are safer.

## 7. Open-Note Review
- Edge cases: Empty, One, Many, Extremes, None, Wrong type
- Guard clause pattern: check None → check type → check empty → happy path
- `if not data:` catches empty lists and empty strings
- `if data is None:` specifically catches None
- `isinstance(data, type)` validates input type
- Division by zero: check empty list before `len()` in denominator

## 8. Final Takeaway
Write code that fails safely—add guard clauses at the top of functions to handle edge cases before they cause crashes.

# Elif and refactoring

## 🎯 End goal
- Refactor nested `if/else` checks into a flat `if/elif/else` chain.
- Order conditions correctly (Most Specific → Least Specific).
- Avoid "Unreachable Code".

## 🧠 Core Concepts

### 1. The `elif` Keyword
- **Meaning**: "Else If".
- **Behavior**: Checked ONLY if previous conditions were `False`.
- **Benefit**: Removes indentation levels (The "Arrow" shape code).

### 2. Order Matters
- **Rule**: Logic flows Top-Down. First match wins.
- **Trap**: Checking `> 10` before checking `> 100` makes the `> 100` case unreachable.
- **Fix**: Check `> 100` first.

## 📝 Final shape

### Clean
```python
score = 85

if score >= 90:
    print("A")
elif score >= 80:
    print("B")
else:
    print("Study more")
```

### Annotated
```python
score = 85

if score >= 90:      # False (85 not >= 90)
    print("A")       # Skipped
elif score >= 80:    # True (85 >= 80)
    print("B")       # Runs!
else:                # Skipped because 'elif' matched
    print("Study more")
```

## 🔄 Processes

### Refactoring Strategy
1.  **Identify**: Deeply nested checks on the *same variable*.
2.  **Flatten**: Pull them out to the main indentation level.
3.  **Chain**: Connect them with `elif`.

## ⚡ Associations
- `elif` → "Option B, C, D..."
- First Match Wins → Python stops checking after one True.
- Top-Down → Gravity for code execution.

## ⚠️ Traps
- **Ordering**: `if x > 10` ... `elif x > 100`. (Input 150 triggers `> 10` and skips `> 100`).
- **Disjointed IFs**: Using `if` ... `if` instead of `if` ... `elif`. Python will check *both*, potentially running both.

## 🔍 Truth lines
```text
score = 95
# Bad Order
if score > 50: "Pass"
elif score > 90: "Ace"
-> "Pass" (Oops)

# Good Order
if score > 90: "Ace"
elif score > 50: "Pass"
-> "Ace"
```

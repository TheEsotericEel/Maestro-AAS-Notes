# Logical operators

## 🎯 End goal
- Combine conditions using `and`, `or`.
- Invert conditions using `not`.
- Understand **Short-Circuiting** (Lazy Evaluation).

## 🧠 Core Concepts

### 1. The Operators
- `and`: **Both** must be True.
- `or`: **At least one** must be True.
- `not`: **Flips** True ↔ False.

### 2. Short-Circuiting
- Python stops checking as soon as the answer is known.
- `False and ...` → Stops (Result is False).
- `True or ...` → Stops (Result is True).
- **Use Case**: Safety checks. `if user and user.is_active:` (If user is None, second part doesn't crash).

## 📝 Final shape

### Clean
```python
age = 25
has_id = True

if age >= 21 and has_id:
    print("Entry allowed")
```

### Annotated
```python
age = 25
has_id = True

# Both sides must be True
if age >= 21 and has_id:
    print("Entry allowed")
```

## 🔄 Processes

### Evaluating Logic
1.  **Operator Precedence**: `not` > `and` > `or`.
2.  **Grouping**: Use `()` to force order. `(A or B) and C`.

## ⚡ Associations
- `and` → Multiplying (1 * 1 = 1, anything * 0 = 0)
- `or` → Adding (1 + 0 = 1)
- `not` → Switch

## ⚠️ Traps
- **English Translation**: "If color is red or blue" -> `if color == "red" or "blue":` (WRONG! "blue" is truthy).
  - Correct: `if color == "red" or color == "blue":`
- **Precedence**: `A or B and C` means `A or (B and C)`.

## 🔍 Truth lines
```text
True and True → True
True and False → False
True or False → True
False or False → False
not True → False
not False → True
```

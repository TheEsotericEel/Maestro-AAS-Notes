# String membership with 'in'

## 🎯 End goal
- Check if a substring exists inside a string using `in`.
- Use `not in` to ensure absence.
- Handle Case Sensitivity checks.

## 🧠 Core Concepts

### 1. The `in` Operator
- **Syntax**: `substring in string`
- **Result**: `True` if found, `False` otherwise.
- **Direction**: Left (Needle) in Right (Haystack).

### 2. Case Sensitivity
- **Fact**: `"A"` is not `"a"`.
- **Trap**: `"apple" in "Pineapple"` is `True`.
- **Trap**: `"apple" in "PINEAPPLE"` is `False`.

## 📝 Final shape

### Clean
```python
email = "user@example.com"

if "@" in email:
    print("Valid email format")
else:
    print("Missing @ symbol")
```

### Annotated
```python
email = "user@example.com"

if "@" in email:               # Scans 'email' for '@'
    print("Valid email format")
else:
    print("Missing @ symbol")
```

## 🔄 Processes

### The Search Logic
1.  **Scan**: Python looks through the string character by character.
2.  **Match**: If exact sequence matches, returns True instantly.
3.  **End**: If end reached without match, returns False.

## ⚡ Associations
- `in` → "Is it inside?"
- `not in` → "Is it missing?"
- Needle → Haystack

## ⚠️ Traps
- **Reversed Order**: `"Haystack" in "Needle"` (Wrong way around).
- **Partial Matches**: `"cat" in "cation"` is True. (Watch out for word boundaries).
- **Empty String**: `"" in "anything"` is always True.

## 🔍 Truth lines
```text
"fun" in "function" → True
"Fun" in "function" → False  (Case sensitive)
"a" in "apple" → True
"z" not in "apple" → True
```

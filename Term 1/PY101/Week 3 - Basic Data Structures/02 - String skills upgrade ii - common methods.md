# String skills upgrade ii - common methods

## 🎯 End goal
- Clean text with `strip()`.
- Normalize text with `lower()` / `upper()`.
- Find and Replace content.
- Split strings into lists and Join them back.

## 🧠 Core Concepts

### 1. Immutability
- **Fact**: Strings CANNOT be changed.
- **Consequence**: All methods return a **NEW** string.
- **Rule**: If you don't save the result (`x = x.lower()`), the work is lost.

### 2. The Big 5 Methods
- `strip()`: Removes whitespace from ends.
- `lower()`: Converts to lowercase.
- `replace(old, new)`: Swaps content.
- `find(sub)`: Returns index of first match (or -1).
- `split(sep)`: Chops string into a list.

## 📝 Final shape

### Clean
```python
raw = "  User@Example.COM  "
clean = raw.strip().lower()

if "@" in clean:
    parts = clean.split("@")
    print(f"User: {parts[0]}")
```

### Annotated
```python
raw = "  User@Example.COM  "

# 1. strip() removes spaces -> "User@Example.COM"
# 2. lower() makes it "user@example.com"
clean = raw.strip().lower()

if "@" in clean:
    parts = clean.split("@")   # ["user", "example.com"]
    print(f"User: {parts[0]}") # "user"
```

## 🔄 Processes

### Data Cleaning Pipeline
1.  **Strip**: Remove garbage spaces. `s.strip()`
2.  **Normalize**: Standardize case. `s.lower()`
3.  **Process**: Extract or validate data.

## ⚡ Associations
- `find()` → Index (or -1)
- `index()` → Index (or Crash)
- `split()` → String comes in, List goes out
- `join()` → List comes in, String goes out

## ⚠️ Traps
- **The "Void" Trap**: Calling `text.upper()` and expecting `text` to change. (It won't).
- **Find vs Index**: `find` is safer because it returns `-1` instead of crashing if missing.
- **Split Empty**: `"".split(",")` returns `['']` (a list with one empty string), not `[]`.

## 🔍 Truth lines
```text
s = " Hello "
s.strip() → "Hello"
s → " Hello " (Original unchanged)

"A".lower() → "a"
"a".upper() → "A"

"Hi-ya".split("-") → ["Hi", "ya"]
"-".join(["A", "B"]) → "A-B"

"Python".find("th") → 2
"Python".find("z") → -1
```

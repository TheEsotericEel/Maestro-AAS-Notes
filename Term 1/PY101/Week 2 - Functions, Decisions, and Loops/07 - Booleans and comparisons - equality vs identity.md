# Booleans and comparisons - equality vs identity

## 🎯 End goal
- Store result of comparisons in **Boolean** variables (`True` / `False`).
- Distinguish **Equality** (`==`) from **Identity** (`is`).
- Use `is None` to check for empty values.

## 🧠 Core Concepts

### 1. Booleans
- **Values**: `True`, `False` (Capitalized!).
- **Source**: Created by comparisons (`>`, `<`, `==`, `!=`).

### 2. Equality (`==`)
- **Question**: "Do these variables hold the same **Value**?"
- **Usage**: Numbers, Strings, most day-to-day checks.
- **Example**: `5 == 5.0` is `True`.

### 3. Identity (`is`)
- **Question**: "Are these variables pointing to the **Same Object** in memory?"
- **Usage**: Checking for `None`.
- **Example**: `x is None`.

## 📝 Final shape

### Clean
```python
is_active = True
score = 100

if is_active and score == 100:
    print("Winner")
```

### Annotated
```python
is_active = True        # Boolean assignment
score = 100

# Comparison (score == 100) becomes True or False
if is_active and score == 100:
    print("Winner")
```

## 🔄 Processes

### The Comparison Check
1.  **Expression**: `x > 5`
2.  **Evaluate**: Python checks the math.
3.  **Result**: Replaces expression with `True` or `False`.

## ⚡ Associations
- `==` → Same Value
- `is` → Same Object (Memory Address)
- `!=` → Not Equal

## ⚠️ Traps
- **Single `=`**: `if x = 5` (SyntaxError). Always use `==` for comparison.
- **Comparing Float/Int**: `5 == 5.0` is True, but `5 is 5.0` is False (different types/objects).
- **String Identity**: `s1 is s2` *might* work for small strings, but always use `==` for text to be safe.

## 🔍 Truth lines
```text
5 == 5.0 → True
5 is 5.0 → False
"a" == "a" → True
None == None → True
None is None → True
```

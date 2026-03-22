# Decision tables to branching logic

## 🎯 End goal
- Translate a Logic Table (Rows/Columns) into Code (`if/elif/else`).
- Ensure **Completeness** (All cases covered).
- Ensure **Exclusivity** (No cases overlap).

## 🧠 Core Concepts

### 1. The Mapping
- **Table Row** → **Code Branch**.
- **Conditions** → **Expressions** (`if x < 10`).
- **Actions** → **Body** (`print("Small")`).

### 2. Completeness (The `else`)
- **Question**: "What if the input is something weird?"
- **Solution**: Always have an `else` branch to handle "Everything else" or raise an error.

### 3. Exclusivity
- **Question**: "Can an input trigger two rows?"
- **Solution**: Use `elif` (structures exclusivity by definition) and correct standard boundaries.

## 📝 Final shape

### Clean
```python
# Table:
# < 0   -> Error
# 0-100 -> Valid
# > 100 -> Error

amt = 50

if amt < 0:
    print("Error: Negative")
elif amt <= 100:
    print("Valid")
else:
    print("Error: Too High")
```

### Annotated
```python
amt = 50

if amt < 0:           # Row 1
    print("Error: Negative")
elif amt <= 100:      # Row 2 (Implicitly >= 0 due to 'elif')
    print("Valid")
else:                 # Row 3 (Implicitly > 100)
    print("Error: Too High")
```

## 🔄 Processes

### The Translation
1.  **Read Row 1**: "If X is negative..." → `if x < 0:`
2.  **Read Row 2**: "If X is between..." → `elif x <= 100:`
3.  **Read Row 3**: "Otherwise..." → `else:`

## ⚡ Associations
- Row → Branch
- Top Row → `if`
- Middle Rows → `elif`
- Bottom Row → `else`

## ⚠️ Traps
- **Gaps**: Handling `< 10` and `> 10` but forgetting `== 10`.
- **Duplicate Coverage**: Two `if` statements that both match. Use `elif` to force one-or-the-other.

## 🔍 Truth lines
```text
# Input: 10
if x < 10: "A"
elif x > 10: "B"
else: "C"
-> "C" (Because 10 is not < 10 and not > 10)
```

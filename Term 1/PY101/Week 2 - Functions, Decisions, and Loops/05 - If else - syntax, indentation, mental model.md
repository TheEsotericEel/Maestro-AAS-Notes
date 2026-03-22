# If else - syntax

## 🎯 End goal
- Use `if` to run code **conditionally**.
- Use `else` to define a **default** path.
- Master **Indentation** as the way to define blocks.

## 🧠 Core Concepts

### 1. The Syntax
- **Header**: `if <condition>:`
- **Body**: Indented block runs ONLY if condition is True.
- **Else**: `else:` (no condition) followed by indented block.

### 2. The Condition
- Must evaluate to **True** or **False**.
- Comparisons: `==`, `!=`, `>`, `<`, `>=`, `<=`.

### 3. Indentation
- Python uses whitespace to see where blocks start/end.
- Standard: 4 spaces.

## 📝 Final shape

### Clean
```python
age = 20

if age >= 18:
    print("Vote")
    print("Drive")
else:
    print("Wait")

print("Done")
```

### Annotated
```python
age = 20

if age >= 18:       # Check condition
    print("Vote")   # Runs if True
    print("Drive")  # Runs if True
else:               # Default path
    print("Wait")   # Runs if False

print("Done")       # Always runs (unindented)
```

## 🔄 Processes

### The Branching Logic
1.  **Check**: Evaluate `if` condition.
2.  **True?**: Run `if` block. Skip `else`.
3.  **False?**: Skip `if` block. Run `else`.
4.  **Rejoin**: Continue with unindented code below.

## ⚡ Associations
- `if` → "Maybe"
- `else` → "Otherwise"
- Colon `:` → "Block follows"
- `==` → Comparison (Is it equal?)
- `=` → Assignment (Make it equal)

## ⚠️ Traps
- **Assignment inside If**: `if x = 5:` is a SyntaxError. Use `==`.
- **Missing Colon**: `if x > 5` (SyntaxError).
- **Bad Indentation**: `IndentationError` usually means lines don't line up.

## 🔍 Truth lines
```text
x = 10
if x > 5: print("Big") → Big
if x < 5: print("Small") → (nothing)

if True: print("Yes") else: print("No") → Yes
if False: print("Yes") else: print("No") → No
```

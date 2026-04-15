# For loops and range()

## 🎯 End goal
- Repeat code a specific number of times using `for` and `range()`.
- Understand the 3 forms of `range()`.
- Use the loop variable `i` inside the loop.

## 🧠 Core Concepts

### 1. The `range()` Function
- **`range(stop)`**: 0 to `stop - 1`. (e.g., `range(5)` → 0, 1, 2, 3, 4).
- **`range(start, stop)`**: `start` to `stop - 1`. (e.g., `range(1, 4)` → 1, 2, 3).
- **`range(start, stop, step)`**: Jumps by `step`. (e.g., `range(0, 10, 2)` → 0, 2, 4, 6, 8).

### 2. The Loop Structure
- **Syntax**: `for <var> in <sequence>:`
- **Behavior**: Assigns next value to `<var>`, runs body, repeats until sequence empty.

## 📝 Final shape

### Clean
```python
total = 0
for i in range(1, 6):
    print(f"Adding {i}")
    total = total + i

print(f"Sum: {total}")
```

### Annotated
```python
total = 0

# i takes values 1, 2, 3, 4, 5
for i in range(1, 6):
    print(f"Adding {i}")
    total = total + i     # Accumulate

print(f"Sum: {total}")
```

## 🔄 Processes

### The Accumulator Pattern
1.  **Init**: Create variable *before* loop (`total = 0`).
2.  **Loop**: Iterate through numbers.
3.  **Add**: Update variable inside loop (`total += i`).
4.  **Result**: Use variable *after* loop.

## ⚡ Associations
- `range(n)` → Repeat n times
- `i` → The current counter
- Indentation → The "Repeat Block"

## ⚠️ Traps
- **Off-by-one**: `range(1, 5)` stops at 4, not 5.
- **Resetting inside loop**: `for i in range(5): total = 0` (Wipes memory every time).
- **Variable Name**: Don't use `sum` or `list` (shadows built-ins). Use `total`.

## 🔍 Truth lines
```text
range(3) → 0, 1, 2
range(1, 4) → 1, 2, 3
range(0, 10, 5) → 0, 5
range(3, 0, -1) → 3, 2, 1
```

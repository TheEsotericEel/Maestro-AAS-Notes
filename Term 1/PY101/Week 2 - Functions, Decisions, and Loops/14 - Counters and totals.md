# Counters and totals

## 🎯 End goal
- Use **Counters** to track occurrences (`count += 1`).
- Use **Totals** to sum values (`total += value`).
- Initialize variables correctly to avoid `NameError`.

## 🧠 Core Concepts

### 1. The Initializer
- **Rule**: Variables must exist before you add to them.
- **Value**: usually `0` for sums, `""` for string building, `[]` for lists.
- **Placement**: MUST be *outside* (before) the loop.

### 2. The Update
- **Counter**: `count = count + 1` (Counts *iterations*).
- **Accumulator**: `total = total + price` (Sums *data*).

## 📝 Final shape

### Clean
```python
prices = [10, 20, 5]
count = 0
total = 0

for p in prices:
    count = count + 1
    total = total + p

print(f"Items: {count}, Total: ${total}")
```

### Annotated
```python
count = 0  # Start at zero
total = 0

for p in prices:
    count = count + 1  # Add 1 for every item
    total = total + p  # Add the item's price

# Results valid here
print(f"Items: {count}, Total: ${total}")
```

## 🔄 Processes

### Verification
- **Zero Check**: If loop runs 0 times, is the result correct? (Yes, 0).
- **One Check**: If loop runs 1 time, is result correct? (Yes, value of first item).

## ⚡ Associations
- `+=` → Shortcut operator (`x += 1` is `x = x + 1`)
- Initialization → Setting the stage
- Accumulation → Rolling snowball

## ⚠️ Traps
- **Resetting inside loop**: `for x in list: total = 0 ...` (Result will just remain last item).
- **Uninitialized Var**: `total += 5` without `total = 0` first → NameError.

## 🔍 Truth lines
```text
total = 0
for x in [1, 2, 3]: total += x
-> 6

count = 0
for x in [1, 2, 3]: count += 1
-> 3
```

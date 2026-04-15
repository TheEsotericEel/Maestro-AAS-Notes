# Lists iii - mastering list iteration

## 🎯 End goal
- Loop through lists using `for x in list`.
- **Filter pattern**: Create new list with selected items.
- **Map pattern**: Create new list with transformed items.

## 🧠 Core Concepts

### 1. The Loop
- **Syntax**: `for item in items_list:`
- **Reading**: "For each item in the list of items..."
- **Scope**: `item` is a local variable updated every iteration.

### 2. The Accumulator / Buffer Pattern
- **Start**: `result = []` (Empty list).
- **Loop**: Iterate source.
- **Logic**: `if condition:` or `new_val = transform(item)`.
- **Add**: `result.append(val)`.

## 📝 Final shape

### Clean
```python
scores = [50, 90, 40, 80]
passing = []

for s in scores:
    if s >= 60:
        passing.append(s)

print(passing)
```

### Annotated
```python
scores = [50, 90, 40, 80]
passing = []           # 1. Init empty buffer

for s in scores:       # 2. Iterate
    if s >= 60:        # 3. Check condition
        passing.append(s) # 4. Add to buffer

print(passing)         # [90, 80]
```

## 🔄 Processes

### The Filter Algorithm
1.  Create empty `out_list`.
2.  Look at first item of `in_list`.
3.  Keep it? If yes, `append` to `out_list`.
4.  Repeat for all items.

## ⚡ Associations
- `append()` → Add to end
- `[]` → The bucket
- `for` → The worker

## ⚠️ Traps
- **Modifying while iterating**: Never remove items from a list *while* looping over it. It messes up the internal index.
  - *Fix*: Loop over a copy (`for x in L[:]:`) or build a new list (Filter Pattern).
- **Resetting inside loop**: `result = []` inside the loop wipes your progress every round.

## 🔍 Truth lines
```text
nums = [1, 2, 3]
dbl = []
for n in nums: dbl.append(n * 2)
dbl → [2, 4, 6]
```

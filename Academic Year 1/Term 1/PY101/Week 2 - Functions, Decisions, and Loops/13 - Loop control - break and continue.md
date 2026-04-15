# Loop control - break and continue

## 🎯 End goal
- Use `break` to **Eject** from a loop early.
- Use `continue` to **Skip** the rest of the current round.
- Combine with `if` to filter data processing.

## 🧠 Core Concepts

### 1. Break (The Eject Button)
- **Action**: Immediately terminates the *entire* loop.
- **Jump**: Execution resumes *after* the loop body.
- **Use Case**: Finding a needle in a haystack (Stop once found).

### 2. Continue (The Skip Button)
- **Action**: Immediately stops the *current iteration*.
- **Jump**: Execution goes back to the *top* (Condition check / Next item).
- **Use Case**: Filtering bad data (Skip errors, process valid items).

## 📝 Final shape

### Clean
```python
for i in range(10):
    if i == 3:
        continue
    if i == 8:
        break
    print(i)
```

### Annotated
```python
for i in range(10):
    if i == 3:
        continue  # Skip 3, go to 4
    if i == 8:
        break     # Stop everything at 8
    print(i)      # Runs for 0,1,2,4,5,6,7
```

## 🔄 Processes

### The Search Pattern
1.  **Loop**: Iterate through items.
2.  **Check**: `if item == target:`
3.  **Found**: Save result and `break`.

## ⚡ Associations
- `break` → "I'm done"
- `continue` → "Next please"
- Infinite Loop → `while True:` (Safe only with `break`)

## ⚠️ Traps
- **Break Only Exits One Loop**: In nested loops, `break` only kills the inner one.
- **Continue in While**: If you skip the "Update" line, you get an infinite loop!
  - *Fix*: Update counter *before* continue.

## 🔍 Truth lines
```text
for i in range(3):
    if i == 1: break
    print(i)
-> 0

for i in range(3):
    if i == 1: continue
    print(i)
-> 0, 2
```

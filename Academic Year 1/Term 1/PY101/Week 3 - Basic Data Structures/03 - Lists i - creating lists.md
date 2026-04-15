# Lists i - creating lists

## 🎯 End goal
- Create lists using `[]`.
- Create lists from ranges using `list(range(...))`.
- Understand Lists as **Ordered, Mutable Sequences**.
- Get the length using `len()`.

## 🧠 Core Concepts

### 1. The Box Model
Think of a list as a row of numbered boxes.
- **Ordered**: Items stay in the order you put them.
- **Mutable**: You can swap the contents of a box later.
- **Heterogeneous**: Boxes can hold anything (numbers, strings, even other lists).

### 2. Syntax
- **Literal**: `[item1, item2, ...]`
- **Constructor**: `list(iterable)`

## 📝 Final shape

### Clean
```python
scores = [10, 20, 30]
scores[0] = 99
print(len(scores))
```

### Annotated
```python
# Create a list with 3 integers
scores = [10, 20, 30]

# Change the first item (Mutable!)
scores[0] = 99   # List is now [99, 20, 30]

# Count items
print(len(scores)) # 3
```

## 🔄 Processes

### The Range Trick
1.  `range(5)` → Abstract sequence (0, 1, 2, 3, 4)
2.  `list(range(5))` → Concrete list `[0, 1, 2, 3, 4]`
3.  **Why?**: Range saves memory. List takes memory but lets you edit items.

## ⚡ Associations
- `[]` → Empty List
- `len(L)` → Count of items
- `Mutable` → Changeable
- `Ordered` → First stays first

## ⚠️ Traps
- **Variable Names**: Don't name your list `list`. (It kills the `list()` function).
- **Index vs Length**: Length is 3, but last index is 2. `L[3]` crashes.
- **Trailing Comma**: `colors = ["Red", "Blue",]` is valid (and good style for multi-line lists).

## 🔍 Truth lines
```text
L = [1, 2, 3]
len(L) → 3
L[0] = 5
L → [5, 2, 3]

list(range(3)) → [0, 1, 2]
list("ABC") → ['A', 'B', 'C']
```

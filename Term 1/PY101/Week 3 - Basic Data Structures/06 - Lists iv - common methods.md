# Lists iv - common methods

## 🎯 End goal
- Add items: `append()` vs `extend()` vs `insert()`.
- Remove items: `pop()` vs `remove()`.
- Search: `index()` and `count()`.
- Organize: `sort()` and `reverse()`.

## 🧠 Core Concepts

### 1. Adding: The Append/Extend Split
- **`append(item)`**: "Add this *object* as one slot."
  - `L.append([1, 2])` → `[..., [1, 2]]` (Nested list).
- **`extend(iterable)`**: "Pour these *contents* into slots."
  - `L.extend([1, 2])` → `[..., 1, 2]` (Flat add).

### 2. Removing: Index vs Value
- **`pop(i)`**: Remove by **Index**. Returns the item. (Defaults to last).
- **`remove(val)`**: Remove by **Value**. No return. Finds first match only.

## 📝 Final shape

### Clean
```python
stack = ["Page1"]
stack.append("Page2")
last = stack.pop() 

users = ["Alex", "Bob", "Alex"]
users.remove("Alex")
```

### Annotated
```python
stack = ["Page1"]
stack.append("Page2")      # ["Page1", "Page2"]
last = stack.pop()         # Removes "Page2", returns it.

users = ["Alex", "Bob", "Alex"]
users.remove("Alex")       # Removes FIRST "Alex" only.
# users is ["Bob", "Alex"]
```

## 🔄 Processes

### The Stack Pattern (LIFO)
1.  **Push**: `L.append(item)`
2.  **Pop**: `item = L.pop()`
3.  **Result**: Last In, First Out.

## ⚡ Associations
- `append` → +1 Item
- `extend` → +N Items
- `pop` → Remove & Return
- `remove` → Delete First Match

## ⚠️ Traps
- **`remove` crash**: If value isn't found, `ValueError`. Check `if x in L:` first.
- **Sorting returns None**: `x = L.sort()` makes `x` None! `sort()` changes L *in-place*.
  - Use `sorted(L)` if you want a new list returned.

## 🔍 Truth lines
```text
L = [1]
L.append([2]) → [1, [2]]
L.extend([3]) → [1, [2], 3]
L.pop() → 3
L.remove([2]) → [1]
```

# Ordering lists - sorted() vs .sort()

## 🎯 End goal
- Sort lists permanently using `.sort()`.
- Sort lists temporarily (new copy) using `sorted()`.
- Sort in reverse order.

## 🧠 Core Concepts

### 1. The Surgeon vs The Photocopier
- **`.sort()` (The Surgeon)**: Operates on the patient directly. Changes the original list. Returns `None`.
- **`sorted()` (The Photocopier)**: Takes a photo, rearranges the photo, and gives you the **New Image**. Original list stays untouched.

### 2. Direction
- Default: Ascending (0→9, A→Z).
- Reverse: `reverse=True` (9→0, Z→A).

## 📝 Final shape

### Clean
```python
nums = [3, 1, 2]

# Option A: New List
ordered = sorted(nums)

# Option B: Modify In-Place
nums.sort()
```

### Annotated
```python
nums = [3, 1, 2]

# Option A: Safety
ordered = sorted(nums)   # nums is still [3, 1, 2]
print(ordered)           # [1, 2, 3]

# Option B: Commitment
nums.sort()              # nums becomes [1, 2, 3]
print(nums)
```

## 🔄 Processes

### Choosing the Right Tool
1.  **Do you need the old order later?**
    - **YES**: Use `y = sorted(x)`.
    - **NO**: Use `x.sort()`.

## ⚡ Associations
- `sorted()` → Returns Data
- `.sort()` → Returns None
- `reverse=True` → Flip it

## ⚠️ Traps
- **Assigning .sort()**: `x = L.sort()` sets `x` to `None`!
- **Mixed Types**: `[1, "A"].sort()` crashes (cannot compare Int and Str).

## 🔍 Truth lines
```text
L = [2, 1]
sorted(L) → [1, 2]
L → [2, 1] (Unchanged)

L.sort()
L → [1, 2] (Changed)

x = L.sort()
print(x) → None
```

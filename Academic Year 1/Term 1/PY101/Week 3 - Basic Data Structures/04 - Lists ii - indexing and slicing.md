# Lists ii - indexing and slicing

## 🎯 End goal
- Access and Modify items using **Index**.
- Extract sublists using **Slicing**.
- Understand that Slicing creates a **New List** (Copy).

## 🧠 Core Concepts

### 1. The Index Map (Same as Strings!)
```text
 List: [ "A" , "B" , "C" , "D" ]
 Index:   0     1     2     3
 Neg:    -4    -3    -2    -1
```

### 2. Mutation via Index
- **Read**: `val = L[0]`
- **Write**: `L[0] = "New"` (Works because lists are mutable)

### 3. Slicing Behavior
- `L[start:stop]` creates a **Shallow Copy** of that section.
- Changing the *copy* does NOT change the *original*.

## 📝 Final shape

### Clean
```python
foods = ["Pizza", "Taco", "Sushi"]
foods[1] = "Burrito"

top_two = foods[:2]
```

### Annotated
```python
foods = ["Pizza", "Taco", "Sushi"]

# Mutation: Replace item at index 1
foods[1] = "Burrito"   # ["Pizza", "Burrito", "Sushi"]

# Slicing: Copy first 2 items
top_two = foods[:2]    # ["Pizza", "Burrito"]
```

## 🔄 Processes

### The Copy Logic
1.  **Instruction**: `sub = L[1:3]`
2.  **Action**: Python goes to index 1.
3.  **Copy**: Reads items up to (not including) index 3.
4.  **Create**: Makes a NEW list in memory with those items.
5.  **Assign**: `sub` points to the new list.

## ⚡ Associations
- `L[i]` → Item access
- `L[a:b]` → Sublist copy
- `L[:]` → Full copy of list

## ⚠️ Traps
- **IndexError**: `L[10]` crashes if len is 5.
- **Slice Forgiveness**: `L[0:100]` does NOT crash even if len is 5. It just gives all 5.
- **Reference Confusion**: `A = B` isn't a copy (it's an alias). `A = B[:]` IS a copy.

## 🔍 Truth lines
```text
L = [10, 20, 30]
L[-1] → 30
L[:2] → [10, 20]
L[1] = 99
L → [10, 99, 30]
```

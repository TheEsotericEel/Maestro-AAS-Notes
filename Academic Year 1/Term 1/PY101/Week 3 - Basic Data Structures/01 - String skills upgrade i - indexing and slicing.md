# String skills upgrade i - indexing and slicing

## 🎯 End goal
- Access characters using **0-based Indexing**.
- Extract substrings using **Slicing**.
- Use **Negative Indices** to count from the end.

## 🧠 Core Concepts

### 1. The Index Map
Strings are ordered sequences. Every character has a number.

```text
 P   y   t   h   o   n
 0   1   2   3   4   5  (Positive Index)
-6  -5  -4  -3  -2  -1  (Negative Index)
```

### 2. Slicing Syntax
- **Form**: `[start : stop : step]`
- **Start**: Inclusive (The slice starts *here*).
- **Stop**: Exclusive (The slice stops *before* this).
- **Step**: Jump size (Optional, defaults to 1).

## 📝 Final shape

### Clean
```python
text = "Python"

first = text[0]
last = text[-1]
middle = text[1:4]
reversed_text = text[::-1]
```

### Annotated
```python
text = "Python"

first = text[0]        # "P" (Index 0)
last = text[-1]        # "n" (Last item)
# Start at 1 ('y'), stop before 4 ('o')
middle = text[1:4]     # "yth"
reversed_text = text[::-1] # "nohtyP" (Step -1 flips it)
```

## 🔄 Processes

### The Slice Logic
1.  **Start**: Look at the index.
2.  **Keep Going**: Take characters...
3.  **Stop**: ...until you hit the `stop` index. (Do NOT take the stop index).

## ⚡ Associations
- `0` → First element
- `-1` → Last element
- `:` → "Everything" or "Range"
- `IndexError` → You went off the map

## ⚠️ Traps
- **Stop is Exclusive**: `text[0:3]` gives indices 0, 1, 2. (3 items). It does NOT include index 3.
- **Out of Range**: `text[100]` crashes. `text[0:100]` is safe (just gives what it has).
- **Immutable**: `text[0] = "J"` is a TypeError. You cannot change a string.

## 🔍 Truth lines
```text
s = "Python"
s[0] → "P"
s[5] → "n"
s[-1] → "n"
s[0:2] → "Py"
s[:2] → "Py" (Implicit start 0)
s[2:] → "thon" (Implicit end)
s[:] → "Python" (Copy)
s[::2] → "Pto" (Every 2nd char)
s[::-1] → "nohtyP"
```

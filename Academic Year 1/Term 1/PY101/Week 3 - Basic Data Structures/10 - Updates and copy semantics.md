# Updates and copy semantics

## 🎯 End goal
- Understand **Variables as Labels** (References).
- Distinguish **Aliasing** (`a = b`) from **Copying** (`a = b[:]`).
- Avoid bugs caused by unintended mutation.

## 🧠 Core Concepts

### 1. The Remote Control Model
- **Object**: The TV (Actual list in memory).
- **Variable**: The Remote Control.
- **Assignment (`a = b`)**: Gives you a *second remote* for the *same TV*.
- **Consequence**: Changing channel with Remote A changes what Remote B sees.

### 2. Shallow Copy
- **Slicing (`b = a[:]`)**: Buys a *new TV* that looks just like the old one.
- **Consequence**: Changing channel on New TV doesn't affect Old TV.

## 📝 Final shape

### Clean
```python
original = [1, 2, 3]
alias = original
copy = original[:]

original[0] = 99
```

### Annotated
```python
original = [1, 2, 3]   # TV #1 created

alias = original       # 2nd Remote for TV #1
copy = original[:]     # TV #2 created (looks like #1)

original[0] = 99       # Change channel on TV #1
# alias sees [99, 2, 3] (It's watching TV #1)
# copy sees [1, 2, 3]   (It's watching TV #2)
```

## 🔄 Processes

### The Mutation Test
1.  Change `list_A`.
2.  Did `list_B` change?
    - **Yes**: They are aliases (Same object).
    - **No**: They are copies (Different objects).

## ⚡ Associations
- `=` → Alias / Reference
- `[:]` → Shallow Copy (List)
- `.copy()` → Shallow Copy (Dict/List)
- `id(x)` → Memory Address (The "Serial Number")

## ⚠️ Traps
- **Function Arguments**: Passing a list to a function passes the *Remote Control*. If the function changes the list, your list changes!
- **Nested Traps**: Shallow copies only copy the top layer. Be careful with lists inside lists (covered in next lesson).

## 🔍 Truth lines
```text
a = [10, 20]
b = a
a.append(30)
b → [10, 20, 30]

x = [10, 20]
y = x.copy()
x.append(30)
y → [10, 20]
```

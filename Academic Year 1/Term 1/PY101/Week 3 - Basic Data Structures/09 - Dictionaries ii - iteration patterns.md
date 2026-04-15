# Dictionaries ii - iteration patterns

## 🎯 End goal
- Loop over **Keys**.
- Loop over **Values**.
- Loop over **Items** (Both).
- Master **Tuple Unpacking** in loops.

## 🧠 Core Concepts

### 1. The Three Views
- `.keys()`: Just the labels. (Default).
- `.values()`: Just the contents.
- `.items()`: Pairs of `(Label, Content)`.

### 2. Unpacking
Python allows assigning a tuple to multiple variables at once.
- `k, v = ("Name", "Alex")` puts "Name" in `k` and "Alex" in `v`.
- Used extensively in loops.

## 📝 Final shape

### Clean
```python
scores = {"Alex": 10, "Bob": 20}

# Pattern A: Items (Common)
for name, score in scores.items():
    print(f"{name}: {score}")

# Pattern B: Values
total = 0
for s in scores.values():
    total += s
```

### Annotated
```python
scores = {"Alex": 10, "Bob": 20}

# Unpack pair into 'name' and 'score'
for name, score in scores.items():
    print(f"{name}: {score}")

# Ignore keys, just sum values
total = 0
for s in scores.values():
    total += s
```

## 🔄 Processes

### The .items() Loop
1.  Get Next Pair: `("Alex", 10)`
2.  Unpack: `name="Alex"`, `score=10`
3.  Run Body.
4.  Repeat.

## ⚡ Associations
- `for k in D` → Keys (Fastest)
- `for v in D.values()` → Values
- `for k, v in D.items()` → Both (Most Useful)

## ⚠️ Traps
- **Modifying while iterating**: `for k in D: del D[k]` crashes! Use `list(D.keys())` to make a safe copy first.
- **Unpacking Error**: `for k, v in D:` crashes (because `D` yields only keys, not pairs).

## 🔍 Truth lines
```text
D = {"A": 1}
list(D) → ["A"]
list(D.values()) → [1]
list(D.items()) → [("A", 1)]
```

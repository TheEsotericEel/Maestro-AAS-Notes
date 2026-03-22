# Week 7: The Professor's Reference Guide

> "Pseudocode is the language of clear thought."

---

## 1. The 10 Commandments of Pseudocode

1.  **Thou Shalt Not Use Syntax**: No semicolons, no `def`, no `import`. Logic only.
2.  **Thou Shalt Indent**: Indentation defines ownership. Without it, logic is flat and broken.
3.  **Thou Shalt Be Specific**: "Process Data" is a sin. "Calculate Average" is a virtue.
4.  **Thou Shalt Handle Errors**: Input is never perfect. Plan for the chaos.
5.  **Thou Shalt Cover All Paths**: If there is an `IF`, ask "What if not?"
6.  **Thou Shalt Initialize**: Create your variables before you use them.
7.  **Thou Shalt Verify**: Dry run with a Trace Table before touching the keyboard.
8.  **Thou Shalt One-to-One**: One line of Pseudocode ≈ One line of Python (roughly).
9.  **Thou Shalt Not Guess**: If you don't know the output, don't write the line.
10. **Thou Shalt Iterate**: Plan a little, Code a little, Test a little.

---

## 2. The Logic Translation Dictionary

| Logical Concept | Pseudocode Keyword | Python Implementation |
| :--- | :--- | :--- |
| **Input** | `ASK`, `GET`, `READ` | `variable = input("Prompt")` |
| **Output** | `DISPLAY`, `PRINT`, `SHOW` | `print(variable)` |
| **Assignment** | `SET`, `STORE`, `COMPUTE` | `x = 10` |
| **Decision** | `IF / ELSE IF / ELSE` | `if x: ... elif y: ... else:` |
| **Iteration (Count)** | `REPEAT n TIMES` | `for i in range(n):` |
| **Iteration (List)** | `FOR EACH item IN list` | `for item in items:` |
| **Iteration (State)** | `WHILE condition` | `while condition:` |
| **Comparison** | `IS EQUAL`, `IS LESS THAN` | `==`, `<` |

---

## 3. The Trace Table Template

Copy this table to verify your loops.

| Step | Line # | Variable 1 | Variable 2 | Condition | Output |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | 1 | | | | |
| 2 | | | | | |
| 3 | | | | | |

---

## 4. The Standard Patterns Cheat Sheet

### The Accumulator (Sum/Count)
```python
bucket = 0              # 1. Empty Bucket
for item in items:      # 2. Loop
    bucket += item      # 3. Fill Bucket
```

### The Flag (Search)
```python
found = False           # 1. Default to False
for item in items:
    if item == target:
        found = True    # 2. Flip Switch
        break           # 3. Stop
```

### The Filter (Select)
```python
results = []            # 1. Empty List
for item in items:
    if item > 50:
        results.append(item) # 2. Add Match
```

### The Guard Clause (Validation)
```python
if invalid_input:
    print("Error")
    exit()              # 1. Stop immediately
# 2. Safe to continue code here...
```

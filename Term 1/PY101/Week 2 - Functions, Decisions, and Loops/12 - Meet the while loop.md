# Meet the while loop

## 🎯 End goal
- Use `while` loops for **Indefinite Iteration** (Repeat until condition met).
- Avoid **Infinite Loops**.
- Use the **Sentinel Pattern** for user input.

## 🧠 Core Concepts

### 1. The Logic
- **Statement**: "While condition is True, keep doing this."
- **Check**: Condition checked *before* every iteration.
- **Exit**: Loop stops immediately when condition becomes False.

### 2. Infinite Loops
- **Cause**: Condition never becomes False.
- **Fix**: Ensure variables in the condition are *updated* inside the loop.

## 📝 Final shape

### Clean
```python
password = ""

while password != "secret":
    password = input("Enter password: ")
    print("Checking...")

print("Access Granted")
```

### Annotated
```python
password = ""  # Init variable used in condition

# Check condition (Empty string != "secret", so True)
while password != "secret":
    # Update variable (Crucial!)
    password = input("Enter password: ")
    print("Checking...")

print("Access Granted")
```

## 🔄 Processes

### The Sentinel Pattern
1.  **Prime**: Set variable to a "safe" starting value (or ask for first input).
2.  **Test**: `while variable != sentinel:`.
3.  **Process**: Do work.
4.  **Update**: Ask for new input at bottom of loop.

## ⚡ Associations
- `while` → "Repeated If Statement"
- Infinite Loop → "Frozen Program" (Ctrl+C to kill)
- Sentinel → "Stop Sign" value

## ⚠️ Traps
- **Off-by-one Input**: Asking for input *outside* but not *inside* (Infinite loop of old data).
- **Condition Flips**: `while x > 10` runs *as long as* x is big. To stop when x is big, use `while x <= 10`.

## 🔍 Truth lines
```text
x = 0
while x < 3:
    print(x)
    x = x + 1
-> 0, 1, 2
```

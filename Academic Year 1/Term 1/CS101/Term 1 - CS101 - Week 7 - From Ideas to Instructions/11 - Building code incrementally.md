# Incremental Implementation Strategy

> "A complex system that works is invariably found to have evolved from a simple system that worked." — *John Gall*

## 1. The Strategy of Isolation

### What is it?
Incremental Implementation is the practice of writing a small unit of code, verifying it immediately, and only then moving to the next unit. It is the opposite of "Big Bang" coding (writing everything at once and hoping it works).

### Why does it matter?
If you write 100 lines of code and it fails, the error could be anywhere in those 100 lines.
If you write 5 lines, verify they work, and then write 5 more... if it fails, the error is in the **last 5 lines**.

### The Rule of 10
**Never write more than 10 lines of code without running it.**
*   Inputs working? Run it.
*   Loop structure built? Run it.
*   One `if` statement added? Run it.

---

## 2. The Layered Build Protocol

Build your software like a cake, layer by layer.

### Layer 1: The Foundation (Input/Output)
Verify you can get data in and get data out.
```python
# Layer 1
age = int(input("Enter age: "))
print(f"DEBUG: Received {age}")
```
*Run. Verify.*

### Layer 2: The Control Flow (Skeleton)
Verify your loops and logic paths exist, even if empty.
```python
# Layer 2
if age >= 18:
    print("DEBUG: Adult Logic")
else:
    print("DEBUG: Child Logic")
```
*Run. Verify both paths.*

### Layer 3: The Business Logic (Muscle)
Now implement the complex math or rules.
```python
# Layer 3
if age >= 18:
    ticket_price = 20.00
    if is_member:
        ticket_price *= 0.9
```
*Run. Verify math.*

---

## 3. Practical Example: The Order System

**Task**: Calculate total for 3 items with tax.

**Step 1: Verify Input Loop**
```python
total = 0
for i in range(3):
    price = float(input("Price: "))
    print(f"Got {price}")
```
*Status: Working.*

**Step 2: Add Accumulator**
```python
total = 0
for i in range(3):
    price = float(input("Price: "))
    total += price
print(f"Subtotal: {total}")
```
*Status: Working.*

**Step 3: Add Tax**
```python
tax = total * 0.05
final = total + tax
print(f"Final: {final}")
```
*Status: Working.*

**Result**: A bug-free program built in 3 stress-free steps.

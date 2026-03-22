# Week 2 Bonus Information - Functions, Decisions, and Loops

> **Purpose**: Supplementary definitions, examples, and clarifications for Week 2 concepts

---

## Function Call vs Definition

### Visual Distinction

```py
# DEFINITION (creates the function)
def greet(name):           # ← definition starts with "def"
    print("Hello,", name)

# CALL (uses the function)
greet("Alice")             # ← call uses function name with arguments
```

### Key Rule
- **Definition** = Recipe (written once, stored for later)
- **Call** = Using the recipe (happens when code runs)

### Multiple Calls
```py
def add_one(x):
    return x + 1

result1 = add_one(5)        # call 1: returns 6
result2 = add_one(10)       # call 2: returns 11
result3 = add_one(0)        # call 3: returns 1
```

---

## Parameters vs Arguments - Deep Dive

### Parameters (In Definition)
```py
def calculate_total(price, quantity):    # price, quantity are PARAMETERS
    return price * quantity
```

### Arguments (In Call)
```py
calculate_total(10.0, 3)                 # 10.0, 3 are ARGUMENTS
```

### Matching Rule
```py
# Parameters: 2 (price, quantity)
# Arguments: 2 (10.0, 3) ✅ MATCHES

# Parameters: 2 (price, quantity)
# Arguments: 1 (10.0) ❌ ERROR: missing argument
```

### Position Matters
```py
def greet(first, last):
    print(first, last)

greet("Alice", "Smith")      # Alice Smith ✅
greet("Smith", "Alice")      # Smith Alice ❌ (wrong order)
```

---

## Return vs Print - Complete Guide

### Return (Sends Value Back)
```py
def add(a, b):
    return a + b            # sends value to caller

result = add(3, 4)          # result = 7
print(result)               # 7
print(add(5, 2))            # 7 (can use directly)
```

### Print (Displays Only)
```py
def add_print(a, b):
    print(a + b)            # displays, but returns None

result = add_print(3, 4)    # prints: 7
print(result)               # None (function returned nothing)
```

### When to Use Which
- **Return**: When caller needs the value for further computation
- **Print**: When you only want to display output (not reuse the value)

### Combining Both
```py
def calculate_and_show(price, tax_rate):
    total = price * (1 + tax_rate)
    print(f"Total: ${total:.2f}")    # show user
    return total                      # also return for caller

bill = calculate_and_show(100, 0.08)  # prints AND returns
next_bill = bill + 10                  # can use returned value
```

---

## Early Return Pattern

### Concept
When `return` executes, function **immediately exits** - no code after it runs.

```py
def check_age(age):
    if age < 0:
        return "Invalid"     # EXITS HERE if age < 0
    if age < 18:
        return "Minor"       # EXITS HERE if age < 18
    return "Adult"           # Only reached if age >= 18

print(check_age(15))         # Minor
print(check_age(25))         # Adult
print(check_age(-5))         # Invalid
```

### Unreachable Code
```py
def example():
    return 10
    print("This never runs")  # ❌ UNREACHABLE
    return 20                 # ❌ UNREACHABLE
```

---

## Scope: Local vs Global - Complete Picture

### Local Variables (Inside Function)
```py
def calculate():
    total = 100              # LOCAL: exists only inside function
    return total

calculate()
print(total)                 # ❌ NameError: total doesn't exist here
```

### Global Variables (Outside Function)
```py
TAX_RATE = 0.08              # GLOBAL: defined outside function

def add_tax(price):
    return price * (1 + TAX_RATE)  # ✅ Can READ global

result = add_tax(100)
print(result)                # 108.0
```

### Reading vs Modifying Globals
```py
count = 0                    # global

def increment():
    count = count + 1        # ❌ ERROR: can't modify global this way
    return count

# Correct way (if you must modify global - not recommended):
def increment_correct():
    global count             # declare you're using global
    count = count + 1
    return count
```

### Best Practice: Use Parameters
```py
# BAD: Using global
total = 0
def add_to_total(amount):
    global total
    total = total + amount

# GOOD: Use parameters
def add_to_total(current_total, amount):
    return current_total + amount

total = add_to_total(total, 10)  # pass current value, get new value
```

---

## Comparison Operators Complete Reference

| Operator | Meaning | Example | Result |
|----------|---------|---------|--------|
| `==` | Equal to | `5 == 5` | `True` |
| `!=` | Not equal to | `5 != 3` | `True` |
| `<` | Less than | `3 < 5` | `True` |
| `>` | Greater than | `5 > 3` | `True` |
| `<=` | Less than or equal | `5 <= 5` | `True` |
| `>=` | Greater than or equal | `5 >= 3` | `True` |

### Common Mistakes
```py
# WRONG: Using = instead of ==
if age = 18:                # ❌ SyntaxError (assignment, not comparison)

# RIGHT: Using ==
if age == 18:               # ✅ Comparison
```

### String Comparisons
```py
"apple" < "banana"          # True (alphabetical order)
"Z" < "a"                   # True (uppercase < lowercase in ASCII)
"10" < "2"                  # True (string comparison, not numeric!)
```

---

## Boolean Logic Truth Tables

### AND Truth Table
| A | B | A and B |
|---|---|---------|
| True | True | True |
| True | False | False |
| False | True | False |
| False | False | False |

### OR Truth Table
| A | B | A or B |
|---|---|--------|
| True | True | True |
| True | False | True |
| False | True | True |
| False | False | False |

### NOT Truth Table
| A | not A |
|---|-------|
| True | False |
| False | True |

### Complex Examples
```py
# AND: Both must be True
age = 20
has_license = True
if age >= 18 and has_license:
    print("Can drive")      # ✅ Both True

# OR: At least one True
is_weekend = False
is_holiday = True
if is_weekend or is_holiday:
    print("Day off")        # ✅ One is True

# NOT: Flips the value
is_closed = False
if not is_closed:
    print("Open")           # ✅ not False = True
```

---

## Short-Circuiting Explained

### AND Short-Circuit
```py
# If left side is False, right side is NOT evaluated
False and print("This won't print")    # Nothing prints
True and print("This will print")       # Prints: This will print
```

### OR Short-Circuit
```py
# If left side is True, right side is NOT evaluated
True or print("This won't print")      # Nothing prints
False or print("This will print")      # Prints: This will print
```

### Practical Use
```py
# Safe list access (Week 3 preview)
items = [1, 2, 3]
# Check length before accessing (avoids IndexError)
if len(items) > 0 and items[0] == 1:
    print("First item is 1")
```

---

## Equality (`==`) vs Identity (`is`)

### Equality: Same Value
```py
a = 5
b = 5
print(a == b)               # True (same value)

list1 = [1, 2, 3]
list2 = [1, 2, 3]
print(list1 == list2)      # True (same contents)
```

### Identity: Same Object
```py
a = 5
b = 5
print(a is b)               # True (small integers are cached)

list1 = [1, 2, 3]
list2 = [1, 2, 3]
print(list1 is list2)       # False (different objects, same contents)
```

### When to Use `is`
```py
# Use `is` for None
value = None
if value is None:           # ✅ Correct
    print("No value")

if value == None:           # Works but not preferred
    print("No value")
```

### Rule of Thumb
- **`==`**: For comparing values (numbers, strings, list contents)
- **`is`**: For checking `None` or checking if two names point to same object

---

## String Membership (`in`) Patterns

### Basic Membership
```py
text = "Hello, world!"
print("world" in text)      # True
print("Python" in text)     # False
```

### Case Sensitivity
```py
text = "Hello"
print("hello" in text)      # False (case-sensitive)
print("Hello" in text)     # True
```

### Checking Multiple Conditions
```py
message = "System error: connection failed"
if "error" in message:
    print("Error detected")
elif "warning" in message:
    print("Warning detected")
else:
    print("All good")
```

### Not In
```py
email = "user@example.com"
if "@" not in email:
    print("Invalid email")
```

---

## If/Elif/Else Decision Tree

### Structure
```py
if condition1:
    # Block 1
elif condition2:
    # Block 2
elif condition3:
    # Block 3
else:
    # Block 4 (default)
```

### Execution Rules
1. **Only ONE block executes** (first True condition)
2. **Elif only checked if previous conditions were False**
3. **Else only runs if ALL conditions were False**

### Example Flow
```py
score = 85

if score >= 90:              # False, skip
    print("A")
elif score >= 80:            # True! Execute this
    print("B")               # Prints: B
elif score >= 70:            # Not checked (previous was True)
    print("C")
else:                         # Not reached
    print("F")
```

### Common Mistake: Overlapping Conditions
```py
# WRONG: Both can be True
if score >= 80:
    print("B")
if score >= 90:              # ❌ Can run even if first was True
    print("A")

# RIGHT: Order from most specific to least
if score >= 90:
    print("A")
elif score >= 80:            # ✅ Only checked if score < 90
    print("B")
```

---

## Range() Function Complete Guide

### Three Forms

```py
# Form 1: range(stop)
range(5)                     # 0, 1, 2, 3, 4 (stops before 5)

# Form 2: range(start, stop)
range(2, 6)                  # 2, 3, 4, 5 (stops before 6)

# Form 3: range(start, stop, step)
range(0, 10, 2)              # 0, 2, 4, 6, 8 (step by 2)
range(10, 0, -1)             # 10, 9, 8, 7, 6, 5, 4, 3, 2, 1 (count down)
```

### Common Patterns
```py
# Count 1 to 10
for i in range(1, 11):       # 1, 2, 3, ..., 10
    print(i)

# Count even numbers
for i in range(0, 10, 2):    # 0, 2, 4, 6, 8
    print(i)

# Count backwards
for i in range(10, 0, -1):   # 10, 9, 8, ..., 1
    print(i)
```

### Range vs List
```py
# range() is NOT a list (it's a sequence)
r = range(5)
print(r)                     # range(0, 5)
print(list(r))               # [0, 1, 2, 3, 4] (convert to list)
```

---

## For Loop Patterns

### Pattern 1: Counting
```py
for i in range(5):
    print(i)                 # 0, 1, 2, 3, 4
```

### Pattern 2: Accumulation
```py
total = 0
for i in range(1, 6):
    total = total + i        # 1, 3, 6, 10, 15
print(total)                 # 15
```

### Pattern 3: Filtering (with if)
```py
evens = []
for i in range(10):
    if i % 2 == 0:
        evens.append(i)      # [0, 2, 4, 6, 8]
```

### Pattern 4: Early Exit (with break)
```py
for i in range(10):
    if i == 5:
        break                # Exit loop at 5
    print(i)                 # 0, 1, 2, 3, 4
```

---

## While Loop Patterns

### Pattern 1: Counter-Controlled
```py
count = 0
while count < 5:
    print(count)
    count = count + 1        # Must update!
```

### Pattern 2: Sentinel-Controlled
```py
total = 0
number = int(input("Enter number (0 to stop): "))
while number != 0:           # Sentinel: 0
    total = total + number
    number = int(input("Enter number (0 to stop): "))
print("Total:", total)
```

### Pattern 3: Condition-Based
```py
password = ""
while password != "secret":
    password = input("Enter password: ")
print("Access granted")
```

### Pattern 4: Bounded Attempts
```py
attempts = 0
max_attempts = 3
while attempts < max_attempts:
    guess = input("Guess: ")
    if guess == "correct":
        print("You win!")
        break
    attempts = attempts + 1
```

---

## Break vs Continue - Visual Guide

### Break (Exit Loop)
```py
for i in range(5):
    if i == 3:
        break                # Exit immediately
    print(i)                 # 0, 1, 2 (3 never printed)
print("Done")                # Done
```

### Continue (Skip to Next Iteration)
```py
for i in range(5):
    if i == 3:
        continue             # Skip rest of loop body
    print(i)                 # 0, 1, 2, 4 (3 skipped)
print("Done")                # Done
```

### Comparison Table
| Statement | Effect | Loop Continues? |
|-----------|--------|-----------------|
| `break` | Exit loop immediately | No |
| `continue` | Skip to next iteration | Yes |

### While Loop with Continue (Important!)
```py
count = 0
while count < 5:
    count = count + 1        # ✅ Update BEFORE continue
    if count == 3:
        continue             # Skip printing 3
    print(count)             # 1, 2, 4, 5
```

---

## Accumulator vs Counter

### Accumulator (Running Total)
```py
total = 0                    # Initialize to 0
for i in range(1, 6):
    total = total + i        # ACCUMULATE (add to existing)
print(total)                 # 15
```

### Counter (Count Events)
```py
count = 0                    # Initialize to 0
for i in range(10):
    if i % 2 == 0:
        count = count + 1    # COUNT (increment by 1)
print(count)                 # 5 (how many evens)
```

### Both Together
```py
total = 0
count = 0
for i in range(1, 6):
    total = total + i        # Accumulate sum
    count = count + 1        # Count iterations
print(f"Sum: {total}, Count: {count}")  # Sum: 15, Count: 5
```

### Common Mistake: Overwriting
```py
# WRONG: Overwrites instead of accumulates
total = 0
for i in range(1, 4):
    total = i + 2            # ❌ Replaces total each time
print(total)                 # 5 (only last value)

# RIGHT: Accumulates
total = 0
for i in range(1, 4):
    total = total + i        # ✅ Adds to existing
print(total)                 # 6 (1+2+3)
```

---

## Nested Control Structures

### If Inside For
```py
for i in range(10):
    if i % 2 == 0:
        print(f"{i} is even")
    else:
        print(f"{i} is odd")
```

### For Inside If
```py
mode = "count"
if mode == "count":
    for i in range(5):
        print(i)
else:
    print("Not counting")
```

### While Inside For (Rare)
```py
for i in range(3):
    count = 0
    while count < 2:
        print(f"i={i}, count={count}")
        count = count + 1
```

---

## Function Return Patterns

### Return Single Value
```py
def square(x):
    return x * x

result = square(5)           # 25
```

### Return Multiple Values (Tuple)
```py
def divide_with_remainder(a, b):
    quotient = a // b
    remainder = a % b
    return quotient, remainder  # Returns tuple

q, r = divide_with_remainder(17, 5)  # q=3, r=2
```

### Return Early (Guard Clauses)
```py
def safe_divide(a, b):
    if b == 0:
        return None          # Early return for invalid input
    return a / b

result = safe_divide(10, 2)  # 5.0
result = safe_divide(10, 0)  # None
```

### Return vs Print Decision Tree
```
Need value for further computation?
├─ YES → Use return
└─ NO → Use print (or both)
```

---

## Decision Table to Code Translation

### Step-by-Step Process

**Step 1: Read the table**
| Score | Grade |
|-------|-------|
| >= 90 | A |
| >= 80 | B |
| >= 70 | C |
| < 70  | F |

**Step 2: Order from most specific to least**
```py
if score >= 90:
    grade = "A"
elif score >= 80:
    grade = "B"
elif score >= 70:
    grade = "C"
else:
    grade = "F"
```

**Step 3: Test boundaries**
```py
# Test each boundary
score = 90   # Should be A
score = 89   # Should be B
score = 80   # Should be B
score = 79   # Should be C
score = 70   # Should be C
score = 69   # Should be F
```

---

## Loop Invariants (Concept)

### What is a Loop Invariant?
A condition that **must be true** every time the loop body starts.

### Example: Sum Loop
```py
total = 0
for i in range(1, 6):
    # Invariant: total equals sum of numbers processed so far
    total = total + i
    # Invariant still true after update
```

### Using Assert to Check Invariants
```py
total = 0
for i in range(1, 6):
    # Invariant check
    assert total == sum(range(1, i)), "Invariant violated"
    total = total + i
```

---

## Common Loop Mistakes

### Mistake 1: Infinite While Loop
```py
# WRONG: Never updates condition
count = 0
while count < 5:
    print(count)             # ❌ count never changes → infinite loop

# RIGHT: Update inside loop
count = 0
while count < 5:
    print(count)
    count = count + 1        # ✅ Updates condition
```

### Mistake 2: Resetting Accumulator
```py
# WRONG: Resets each iteration
for i in range(5):
    total = 0                # ❌ Resets to 0 each time
    total = total + i

# RIGHT: Initialize before loop
total = 0                    # ✅ Initialize once
for i in range(5):
    total = total + i
```

### Mistake 3: Off-by-One with Range
```py
# Want: 1, 2, 3, 4, 5
for i in range(5):           # ❌ Gives: 0, 1, 2, 3, 4
    print(i)

for i in range(1, 6):        # ✅ Gives: 1, 2, 3, 4, 5
    print(i)
```

---

## Week 2 Mastery Checklist

Before moving to Week 3, you should be able to:

- [ ] Define functions with parameters
- [ ] Call functions with matching arguments
- [ ] Use `return` to send values back
- [ ] Distinguish `return` from `print`
- [ ] Understand local vs global scope
- [ ] Write `if/elif/else` chains correctly
- [ ] Use comparison operators (`==`, `!=`, `<`, `>`, etc.)
- [ ] Combine conditions with `and`, `or`, `not`
- [ ] Use `in` to check string membership
- [ ] Use `for` loops with `range()`
- [ ] Use `while` loops with proper condition updates
- [ ] Use `break` to exit loops early
- [ ] Use `continue` to skip iterations
- [ ] Accumulate values in loops
- [ ] Count events in loops

---

*End of Week 2 Bonus Information*

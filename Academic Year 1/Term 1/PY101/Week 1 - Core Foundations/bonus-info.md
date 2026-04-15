# Week 1 Bonus Information - Core Foundations

> **Purpose**: Supplementary definitions, examples, and clarifications for Week 1 concepts

---

## Quick Reference: String vs Number

### Visual Distinction

```py
# STRINGS (text) - have quotes
"5"          # string
"Hello"      # string
"3.14"       # string (even though it looks like a number)

# NUMBERS - no quotes
5            # int (integer)
3.14         # float (decimal)
-10          # int (negative)
```

### Key Rule
- **Quotes = text** → `+` concatenates, `*` repeats
- **No quotes = number** → `+` adds, `*` multiplies

---

## Variable Reassignment

### Concept
Variables can be **reassigned** (given a new value), replacing the old value.

```py
age = 20
print(age)        # 20

age = 25          # reassign
print(age)        # 25 (old value is gone)

age = age + 1     # read current value, add 1, store back
print(age)        # 26
```

### Important Notes
- Reassignment **replaces** the old value (doesn't add to it)
- You can reassign to a different type: `x = 5` then `x = "hello"` (not recommended, but possible)
- The variable name stays the same; only the value changes

---

## Operator Precedence (PEMDAS)

### Order of Operations
Python follows mathematical order: **Parentheses → Exponents → Multiplication/Division → Addition/Subtraction**

```py
# Examples
2 + 3 * 4        # = 2 + 12 = 14 (multiplication first)
(2 + 3) * 4      # = 5 * 4 = 20 (parentheses first)
10 / 2 * 3       # = 5 * 3 = 15 (left to right for same precedence)
10 / (2 * 3)     # = 10 / 6 = 1.666... (parentheses first)
```

### Common Pattern
```py
# Money calculation pattern
total = 60 - 4 * 7    # = 60 - 28 = 32 (multiplication before subtraction)
total = (60 - 4) * 7  # = 56 * 7 = 392 (parentheses change order)
```

---

## The `None` Value

### Definition
`None` is a special value meaning "nothing" or "no value". It's Python's way of representing emptiness.

```py
# Functions without return give None
def greet(name):
    print("Hello,", name)
    # no return statement

result = greet("Alice")  # prints "Hello, Alice"
print(result)            # None (function returned nothing)
```

### When You See None
- Function that only `print()` but doesn't `return` → returns `None`
- Variable that hasn't been assigned yet → `NameError` (not `None`, but related)
- Explicitly set: `x = None` (means "x has no value")

---

## String Escape Sequences

### Common Escapes
Strings can contain special characters using backslash (`\`):

```py
print("Hello\nWorld")      # \n = newline (starts new line)
# Output:
# Hello
# World

print("He said \"Hi\"")    # \" = literal quote inside string
# Output: He said "Hi"

print("Path: C:\\Users")   # \\ = literal backslash
# Output: Path: C:\Users

print("Tab\there")         # \t = tab (spacing)
# Output: Tab    here
```

### Raw Strings (Preview)
```py
# r"..." treats backslashes literally (no escaping)
print(r"C:\Users\name")    # prints exactly: C:\Users\name
```

---

## Float Precision Issues

### The Problem
Floating-point math can produce tiny rounding errors:

```py
print(0.1 + 0.2)           # 0.30000000000000004 (not exactly 0.3)
print(7.2 + 0.0)           # 7.199999999999999 (not exactly 7.2)
```

### Why This Happens
Computers store decimals in binary, and some decimal numbers can't be represented exactly.

### Solution Pattern (Week 1)
```py
# Always round before displaying money
total = 7.2
rounded = round(total, 2)           # 7.2 (but stored as 7.1999...)
print(f"${rounded:.2f}")           # $7.20 (formatted correctly)
```

---

## Type Coercion vs Explicit Casting

### Automatic Coercion (Limited)
Python does **very little** automatic type conversion:

```py
# These DON'T work (TypeError)
"5" + 3                    # TypeError: can't add string + int
"10" * "2"                 # TypeError: can't multiply strings

# This DOES work (automatic float promotion)
5 + 3.0                    # 8.0 (int promoted to float)
```

### Explicit Casting (What You Must Do)
```py
# Convert string to number
age_text = "25"
age = int(age_text)        # explicit: string → int

# Convert number to string
price = 9.99
price_text = str(price)    # explicit: float → string
```

### Key Takeaway
- **Automatic**: Only int → float (for math)
- **Explicit**: Everything else requires `int()`, `float()`, or `str()`

---

## Common Input() Pitfalls

### Pitfall 1: Forgetting It Returns String
```py
age = input("Age? ")       # user types: 25
print(age + 1)             # TypeError: can't add string + int
# Fix:
age = int(input("Age? "))  # convert immediately
```

### Pitfall 2: Empty Input
```py
name = input("Name? ")      # user presses Enter (empty string)
print("Hello,", name)       # prints: Hello,  (no name)
# Empty string "" is valid, but may not be what you want
```

### Pitfall 3: Non-Numeric Input
```py
age = int(input("Age? "))   # user types: "abc"
# ValueError: invalid literal for int()
# Fix: validate first (covered in later weeks)
```

---

## String Formatting Alternatives

### Method 1: F-strings (Preferred - Week 1)
```py
price = 7.5
print(f"Price: ${price:.2f}")    # Price: $7.50
```

### Method 2: Concatenation
```py
price = 7.5
print("Price: $" + str(price))    # Price: $7.5 (no .2f formatting)
```

### Method 3: Comma in print() (Auto-Space)
```py
price = 7.5
print("Price: $", price)         # Price: $ 7.5 (note the space)
```

### When to Use Which
- **F-strings**: When you need formatting (`.2f`, alignment, etc.)
- **Concatenation**: When you need exact control (no auto-spaces)
- **Comma**: When simple display is enough (auto-adds space)

---

## Variable Naming Conventions

### Snake Case (Python Standard)
```py
# Good names
user_name = "Alice"
total_price = 99.99
is_valid = True

# Bad names
userName = "Alice"          # camelCase (not Python style)
User_Name = "Alice"         # PascalCase (for classes, not variables)
user name = "Alice"         # spaces (SyntaxError)
2name = "Alice"             # starts with digit (SyntaxError)
```

### Rules Summary
- ✅ Use lowercase letters and underscores: `snake_case`
- ✅ Can include digits, but not at the start: `name1` ✅, `1name` ❌
- ✅ No spaces: `user name` ❌
- ✅ Descriptive: `x` ❌, `total_price` ✅

---

## Division Operators Summary Table

| Operator | Name | Returns | Example | Result |
|----------|------|---------|---------|--------|
| `/` | True division | `float` | `7 / 3` | `2.333...` |
| `//` | Floor division | `int` | `7 // 3` | `2` |
| `%` | Modulus | `int` | `7 % 3` | `1` |

### Quick Rules
- `/` → Always gives decimal (even `8 / 2` → `4.0`)
- `//` → Whole number quotient (drops remainder)
- `%` → Just the remainder

### Identity Check
```py
# Always true: dividend = divisor * quotient + remainder
total = 55
size = 12
quotient = total // size      # 4
remainder = total % size      # 7
print(total == size * quotient + remainder)  # True
```

---

## Modulo Patterns Cheat Sheet

### Even/Odd
```py
n % 2 == 0    # True if even
n % 2 == 1    # True if odd (or n % 2 != 0)
```

### Cycles (0 to N-1)
```py
# % 3 cycles: 0, 1, 2, 0, 1, 2, ...
for i in range(10):
    print(i % 3)    # 0, 1, 2, 0, 1, 2, 0, 1, 2, 0
```

### "Every Nth" Detection
```py
# Every 3rd item (when counting from 1)
for i in range(1, 10):
    if i % 3 == 0:      # 3, 6, 9
        print("Every 3rd!")
```

### Last Digit
```py
number = 1234
last_digit = number % 10    # 4
```

---

## Type Checking Quick Reference

### Using `type()`
```py
print(type(5))              # <class 'int'>
print(type(5.0))            # <class 'float'>
print(type("5"))            # <class 'str'>
print(type(True))           # <class 'bool'>
print(type(None))           # <class 'NoneType'>
```

### Common Checks
```py
# Check if something is a string
if type(x) == str:
    print("It's a string")

# Check if something is a number
if type(x) == int or type(x) == float:
    print("It's a number")
```

---

## Error Types Summary

| Error Type | When It Happens | Example |
|------------|-----------------|---------|
| `SyntaxError` | Code structure is broken | `print("hello"` (missing `)`) |
| `NameError` | Variable/function not defined | `print(x)` when `x` doesn't exist |
| `TypeError` | Wrong types used together | `"5" + 3` |
| `ValueError` | Right type, wrong value | `int("abc")` |
| `IndexError` | List/string index out of range | `"hello"[10]` |
| `ZeroDivisionError` | Dividing by zero | `10 / 0` |

### Quick Fix Guide
- **SyntaxError** → Check quotes, parentheses, colons
- **NameError** → Check spelling, define variable first
- **TypeError** → Convert types: `int()`, `float()`, `str()`
- **ValueError** → Check input value is valid for conversion

---

## Truth Lines Pattern Explained

### What Are Truth Lines?
Truth lines show: **code → expected output**

```text
print("Hello") → Hello
x = 5 + 3; print(x) → 8
```

### Reading Truth Lines
- `;` separates multiple statements on one line
- `→` means "produces this output"
- Everything after `→` is what you see when you run it

### Example Breakdown
```text
print("Score:", 10) → Score: 10
```
- Code: `print("Score:", 10)`
- Output: `Score: 10` (comma adds space automatically)

---

## Common Calculation Patterns

### Pattern 1: Total After Multiple Purchases
```py
start_money = 100
item1_cost = 20
item2_cost = 15
remaining = start_money - item1_cost - item2_cost
# = 100 - 20 - 15 = 65
```

### Pattern 2: Cost Per Item
```py
total_cost = 30
quantity = 5
cost_per_item = total_cost / quantity
# = 30 / 5 = 6.0
```

### Pattern 3: Full Groups + Leftovers
```py
total_items = 55
group_size = 12
full_groups = total_items // group_size    # 4
leftovers = total_items % group_size      # 7
```

---

## Money Formatting Complete Pattern

### Step-by-Step
```py
# 1. Do the math
coffee = 3.60
sandwich = 3.60
total = coffee + sandwich          # 7.2 (may have precision issues)

# 2. Round to 2 decimals
rounded = round(total, 2)          # 7.2 (cleaned up)

# 3. Format for display
formatted = f"${rounded:.2f}"      # "$7.20"
print(formatted)
```

### Why This Order?
- **Math first**: Get the calculation right
- **Round second**: Fix any float precision issues
- **Format last**: Make it look like money (always 2 decimals)

---

## Quick Debugging Tips

### Tip 1: Print Variable Values
```py
age = int(input("Age? "))
print("[DEBUG] age =", age)    # See what value you actually got
```

### Tip 2: Check Types
```py
value = input("Number? ")
print("[DEBUG] type =", type(value))    # Confirm it's a string
value = int(value)
print("[DEBUG] type =", type(value))    # Confirm it's now int
```

### Tip 3: Test Small Pieces
```py
# Instead of:
total = (price1 + price2) * tax_rate

# Test parts:
subtotal = price1 + price2
print("[DEBUG] subtotal =", subtotal)
total = subtotal * tax_rate
print("[DEBUG] total =", total)
```

---

## Glossary Additions

### Literal
A value written directly in code (not from a variable):
```py
5           # integer literal
"hello"     # string literal
3.14        # float literal
```

### Expression
Code that produces a value:
```py
5 + 3           # expression (produces 8)
price * 2       # expression (produces a number)
"Hello" + "!"   # expression (produces "Hello!")
```

### Statement
A complete line of code that does something:
```py
x = 5           # assignment statement
print(x)        # print statement
if x > 0:       # if statement
    pass
```

### Mutability
Whether a value can be changed after creation:
- **Immutable**: Can't change (strings, numbers) → create new value
- **Mutable**: Can change (lists, dicts - Week 3)

---

## Practice Scenarios

### Scenario 1: Temperature Converter
```py
# Convert Fahrenheit to Celsius
fahrenheit = float(input("Temperature in F: "))
celsius = (fahrenheit - 32) * 5 / 9
print(f"{fahrenheit}°F = {celsius:.1f}°C")
```

### Scenario 2: Tip Calculator
```py
bill = float(input("Bill amount: $"))
tip_percent = 0.18
tip = bill * tip_percent
total = bill + tip
print(f"Tip: ${tip:.2f}")
print(f"Total: ${total:.2f}")
```

### Scenario 3: Age Checker
```py
age_text = input("Your age: ")
age = int(age_text)
if age >= 18:
    print("Adult")
else:
    print("Minor")
```

---

## Week 1 Mastery Checklist

Before moving to Week 2, you should be able to:

- [ ] Distinguish strings from numbers by quotes
- [ ] Use `+` correctly (concatenation vs addition)
- [ ] Convert between `str`, `int`, and `float`
- [ ] Use `/`, `//`, and `%` correctly
- [ ] Use `% 2` to check even/odd
- [ ] Round and format money with f-strings
- [ ] Read tracebacks and identify error types
- [ ] Use `input()` and convert to numbers
- [ ] Write valid variable names (snake_case)
- [ ] Model word problems as code expressions

---

*End of Week 1 Bonus Information*

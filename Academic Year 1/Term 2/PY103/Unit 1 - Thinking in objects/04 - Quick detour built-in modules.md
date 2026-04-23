> Course: PY103
> Lesson: Built-in Modules

# Built-in Modules

## 1. Lesson Focus
An intro to Python's **built-in modules**, demonstrating how to access pre-written "toolboxes" of code (like `random`, `math`, and `datetime`) using the `import` statement.

---

## 2. Core Concepts

### Module
**Definition:** A collection of related Python code (functions, variables, etc.) that you can reuse by importing it.
* **Analogy:** Think of a large toolbox. Each module is like a specific drawer in that toolbox (e.g., one drawer for screws, one for wires). 

### The `import` Statement
**Definition:** Tells Python to open that specific "toolbox drawer" so you can use its contents.
* You must import a module before you can call its functions. Without the `import` line, Python will throw an error because it doesn't know what you are referencing.

---

## 3. Notable Built-in Modules

| Module | Purpose | Example Method |
|--------|---------|----------------|
| `random` | Generates random numbers or choices | `random.randint(...)` |
| `math` | Contains mathematical operations | `math.sqrt(...)` |
| `datetime` | Works with calendar dates and times | `datetime.date.today()` |

---

## 4. Syntax Pattern

To use a tool from a module, use the following pattern:
1. Load the module (`import module_name`)
2. Use "dot notation" to access the tool (`module_name.function_name(...)`)

```python
import module_name

result = module_name.function_name()
```

---

## 5. Examples in Action

### Rolling a Die (`random`)
```python
import random

# .randint(start, end) returns an integer between start and end (inclusive)
print(random.randint(1, 10)) 
```

### Square Root (`math`)
```python
import math

# .sqrt(num) calculates the square root 
print(math.sqrt(9))  # Output: 3.0 (Returns a float)
```

### Finding Today's Date (`datetime`)
```python
import datetime

# Retrieves the current date
print(datetime.date.today())  # Output e.g., 2026-04-19
```

---

## 6. Common Mistakes & Logic Traps

### Repeating an Event Incorrectly
When trying to simulate multiple events (like rolling two dice), a common mistake is rolling once and doubling the value:

```python
import random

# ❌ INCORRECT: Rolls one die and doubles it. You can never roll a 7!
roll = random.randint(1, 6)
total = roll + roll

# ✅ CORRECT: Rolls two independent dice and adds their values.
roll_1 = random.randint(1, 6)
roll_2 = random.randint(1, 6)
total = roll_1 + roll_2
```

---

## 7. Open-Note Review

- **Module** = a collection of related Python code.
- **`import`** = required command to load the module into your script.
- **Dot notation** (`module.method`) = how you access tools inside the module.
- Each unique random event (like a separate die roll) requires a separate call to `random.randint(...)`.

**Quick self-test**
> Why do we need the line `import random` before calling `random.randint(1, 6)`?
> → Because Python needs to "open" the random module toolbox so the function `randint` actually exists and can be used.

---

## 8. Final Takeaway
Python provides a massive set of built-in functionality through **modules**. Always remember to `import` the specific module you need at the top of your script before attempting to use its functions.

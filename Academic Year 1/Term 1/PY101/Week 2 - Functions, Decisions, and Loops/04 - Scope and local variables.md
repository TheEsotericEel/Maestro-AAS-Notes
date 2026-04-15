# Scope and local variables

## 🎯 End goal
- Distinguish **Local** (inside function) from **Global** (outside) variables.
- Understand that local variables "die" when the function ends.
- Prefer **Passing Data** (parameters/return) over **Sharing Data** (globals).

## 🧠 Core Concepts

### 1. Local Scope (The Las Vegas Rule)
- **Rule**: What happens in the function, stays in the function.
- **Creation**: Variable created *inside* `def`.
- **Lifespan**: Created when function starts, destroyed when it returns.
- **Visibility**: Invisible to the rest of the program.

### 2. Global Scope (The Public Square)
- **Creation**: Variable created at the main indentation level (no indent).
- **Visibility**: Visible everywhere (read-only inside functions unless `global` keyword is used).
- **Danger**: Hard to track who changed it.

## 📝 Final shape

### Clean
```python
tax_rate = 0.08  # Global

def calculate_total(price):
    tax = price * tax_rate  # Local
    return price + tax

print(calculate_total(100))
# print(tax) -> Error
```

### Annotated
```python
tax_rate = 0.08  # Global (usable inside function)

def calculate_total(price):
    # 'tax' is Local. exists only during this call.
    tax = price * tax_rate
    return price + tax

print(calculate_total(100))
# print(tax) -> NameError: name 'tax' is not defined
```

## 🔄 Processes

### The "Pass & Return" Pattern
Instead of relying on globals:
1.  **Pass** needed data as arguments.
2.  **Compute** using local variables.
3.  **Return** the result.

## ⚡ Associations
- Local → Temporary / Private
- Global → Permanent / Public
- Parameter → Special Local Variable

## ⚠️ Traps
- **Shadowing**: If you name a local var `x` inside a function, it hides the global `x`.
- **The "UnboundLocalError"**: Trying to change a global variable inside a function without declaring `global`.
- **Expecting Locals to Survive**: `def set_score(): score = 10`. Calling this does nothing to any `score` outside.

## 🔍 Truth lines
```text
x = 10
def show_x(): print(x)
show_x() → 10 (reads global)

def set_x(): x = 5
set_x()
print(x) → 10 (global x unchanged)
```

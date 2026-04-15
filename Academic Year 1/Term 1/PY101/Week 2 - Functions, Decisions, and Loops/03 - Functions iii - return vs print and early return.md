# Functions iii - return vs print

## 🎯 End goal
- **Return** data back to the caller using `return`.
- Distinguish `print` (Side Effect) from `return` (Output).
- Capture the result in a variable: `result = func()`.

## 🧠 Core Concepts

### 1. The ATM Analogy
- **Print**: The screen shows you your balance. You can see it, but you can't *spend* it.
- **Return**: The slot gives you cash. You can put it in your wallet (`variable`) and use it later.

### 2. The `return` Keyword
- **Action**: Immediately stops the function.
- **Output**: Sends the value back to where variables wait.
- **Default**: If no return is written, Python secretly does `return None`.

## 📝 Final shape

### Clean
```python
def get_tax(price):
    return price * 0.08

my_price = 100
tax_amount = get_tax(my_price)
total = my_price + tax_amount
print(f"Total: {total}")
```

### Annotated
```python
def get_tax(price):
    # Math happens, result is sent back
    return price * 0.08

my_price = 100
# 'get_tax' becomes 8.0. We store it in 'tax_amount'.
tax_amount = get_tax(my_price) 
total = my_price + tax_amount
print(f"Total: {total}")
```

## 🔄 Processes

### The Capture Pattern
1.  **Define**: Function calculates and `return`s.
2.  **Call & Capture**: `x = function()`
3.  **Use**: `print(x + 5)`

## ⚡ Associations
- `return` → Give back
- `print` → Show on screen
- `x = func()` → Capture result
- `func()` (no var) → Result lost

## ⚠️ Traps
- **Returning Print**: `return print("Hi")` returns `None` (because print returns None).
- **Dead Code**: formatting code *after* a `return` line statement will never run.
- **Printing instead of Returning**: If `func()` prints 5, `x = func()` makes `x` be `None`.

## 🔍 Truth lines
```text
def give_five(): return 5
x = give_five()
print(x) → 5

def say_five(): print(5)
x = say_five() → 5 (printed)
print(x) → None
```

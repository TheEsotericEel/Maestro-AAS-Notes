# Functions ii - Inside the function

## 🎯 End goal
- Pass data *into* functions using **Parameters**.
- Distinguish **Parameters** (definition) from **Arguments** (call).
- Use local variables for temporary math.

## 🧠 Core Concepts

### 1. Parameters ( The Slots )
- **Definition**: Variables listed inside the `def (...)`.
- **Role**: They act as "Input Slots" for the function.
- **Scope**: They only exist *inside* the function.

### 2. Arguments ( The Data )
- **Definition**: The actual values sent during the call.
- **Rule**: Order matters! First argument goes to first parameter.

## 📝 Final shape

### Clean
```python
def calculate_total(price, tax):
    total = price + tax
    print(f"Total: ${total:.2f}")

calculate_total(10.00, 0.80)
```

### Annotated
```python
#                  Param1, Param2
def calculate_total(price, tax):
    # 'price' and 'tax' are local variables here
    total = price + tax
    print(f"Total: ${total:.2f}")

#              Arg1, Arg2
calculate_total(10.00, 0.80)
# price becomes 10.00, tax becomes 0.80
```

## 🔄 Processes

### Passing Data
1.  **Call**: `add(5, 3)`
2.  **Match**: 5 → `a`, 3 → `b` (in `def add(a, b):`)
3.  **Run**: Execution enters function with these values.
4.  **Finish**: Function ends, parameters are wiped.

## ⚡ Associations
- Parameters → Parking Spots (Defined names)
- Arguments → Cars (Actual values)
- Comma `,` → Separator

## ⚠️ Traps
- **Argument Mismatch**: Call has 3 args, Definition has 2 params → `TypeError`.
- **Shadowing**: A parameter named `total` hides a global variable named `total`.
- **Hardcoding**: Don't write `def add(a, b): print(5 + 3)`. Write `print(a + b)`.

## 🔍 Truth lines
```text
def show(x): print(x)
show(10) → 10
show("Hi") → Hi
def add(a, b): print(a + b)
add(1, 2) → 3
add("A", "B") → AB
```

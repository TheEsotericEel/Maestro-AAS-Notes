# Lesson 10: Checking the Facts (Type Systems)

## 🎯 End Goal
To identify, verify, and transform the data types of your variables. You will learn to debug "invisible" errors where data looks right but acts wrong.

## 🧠 Core Concepts

### 1. Introspection (`type()`)
Python is an **Object-Oriented** language. Everything—numbers, functions, strings—is an object.
The `type()` function asks an object: "What template were you built from?"
*   **Syntax**: `type(variable_name)`
*   **Result**: `<class 'int'>`, `<class 'str'>`, etc.

### 2. Casting (Constructors)
"Casting" is the act of converting one data type into another. In Python, we do this by calling the **Constructor** function of the target class.
*   `int(x)`: Constructs an Integer from `x`.
*   `float(x)`: Constructs a Float from `x`.
*   `str(x)`: Constructs a String from `x`.

### 3. The "Input" Trap
Data coming from the outside world (user input, text files) **ALWAYS** arrives as a String.
Even if the user types `42`, Python sees `"42"`.
*   **Rule**: You must manually **cast** input to the correct type before doing math.

## 📝 Examples

### The "Invisible" Error
```python
x = "5"
y = 5
print(x * y)
# Output: "55555" (String repetition!)
# Confusing because the user expected: 25
```

### The Fix (Explicit Casting)
```python
x = "5"
y = 5
print(int(x) * y)
# Output: 25
```

### Truncation Behavior
When casting a `float` to an `int`, Python does **NOT** round. It truncates (chops off the decimal).
```python
print(int(3.14)) # 3
print(int(3.99)) # 3 (NOT 4!)
```

## ⚡ Associations
*   **`type()`**: ID Card scanner.
*   **`int()`**: "Make this a whole number."
*   **`str()`**: "Make this text."

## ⚠️ Traps and Pitfalls

| Mistake | Code | Error Type | Why? |
| :--- | :--- | :--- | :--- |
| **Math on Strings** | `"10" / 2` | `TypeError` | You cannot divide text. Cast to `int` first. |
| **Invalid Cast** | `int("Hello")` | `ValueError` | "Hello" does not look like a number. Python cannot convert it. |
| **Decimal String to Int** | `int("3.14")` | `ValueError` | `int()` expects a clean whole number string. You must use `float("3.14")` first. |

## 🔍 Truth Lines
```text
type(5) -> <class 'int'>
type("5") -> <class 'str'>
int(3.99) -> 3
str(10) + "5" -> "105"
int("10") + 5 -> 15
```

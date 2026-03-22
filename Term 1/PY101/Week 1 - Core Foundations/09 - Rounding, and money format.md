# Lesson 09: Rounding and Formatting numbers

## 🎯 End Goal
To distinguish between changing a number's **value** (Rounding) and changing a number's **appearance** (Formatting), and to handle currency with professional precision.

## 🧠 Core Concepts

### 1. Rounding (Data Mutation)
The `round()` function changes the actual data in memory.
*   **Method**: Banker's Rounding (Round Half to Even).
*   **Rule**: If a number is exactly halfway between two integers (x.5), Python rounds to the **nearest even number**.
    *   `2.5` -> `2`
    *   `3.5` -> `4`
*   **Why?**: To prevent statistical bias. If you always rounded .5 *up*, your average sum would continually grow larger than reality. Alternating to evens balances this error out over large datasets.

### 2. Formatting (Presentation)
Formatting changes how the number "looks" as a String, without changing the stored value.
*   **Tool**: F-Strings with format specifiers (`:`)
*   **Syntax**: `f"{value:.2f}"` (Fixed point, 2 decimals).

## 🛠️ The Specifiers

### Currency Style (`.2f`)
```python
price = 19.9
print(f"${price:.2f}") 
# Output: $19.90 (Adds the zero!)
```

### Thousand Separators (`,`)
```python
salary = 50000
print(f"${salary:,}") 
# Output: $50,000 (Adds the comma!)
```

### Combined
```python
large_val = 12345.6789
print(f"${large_val:,.2f}") 
# Output: $12,345.68 (Comma + Rounding for display)
```

## ⚠️ The Floating Point Trap (Again)
Just like `0.1 + 0.2`, rounding floats is dangerous.
```python
print(round(2.675, 2))
# Expected: 2.68
# Actual: 2.67
```
*   **Why**: In binary, 2.675 is actually `2.67499999...`, so it rounds down.
*   **Professional Fix**: For real money, use the `decimal` library (Week 4), or work in cents (Integers).

## 📝 Best Practices: Model vs. View
*   **The Model (Data)**: Store numbers as raw `int` or `float`. Never store "$10.00" in the database.
*   **The View (Display)**: Apply formatting ONLY when printing to the user.

## ⚡ Associations
*   **`round()`**: Changes the math.
*   **`:.2f`**: Changes the look.
*   **Banker's Rounding**: `.5` goes to Even.

## 🔍 Truth Table

| Code | Result | Type | Note |
| :--- | :--- | :--- | :--- |
| `round(1.5)` | `2` | `int` | Nearest Even. |
| `round(2.5)` | `2` | `int` | Nearest Even. |
| `f"{1.5:.2f}"` | `"1.50"` | `str` | Display only. |
| `f"{1000:,}"` | `"1,000"` | `str` | Comma separator. |

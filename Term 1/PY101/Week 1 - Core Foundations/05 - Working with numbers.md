# Lesson 05: Working with Numbers

## 🎯 End Goal
To effectively calculate, count, and measure using Python's numeric types, while avoiding the common logical traps associated with computer arithmetic.

## 🧠 Core Concepts

### 1. The Two Kingdoms: `int` vs `float`
In mathematics, numbers are numbers. In Computer Science, we distinguish between **discrete** and **continuous** values.

| Type | Name | Definition | Example | Purpose |
| :--- | :--- | :--- | :--- | :--- |
| **int** | Integer | Whole numbers. Exact. | `5`, `-42`, `0` | Counting items, loops, indices. |
| **float** | Floating Point | Decimal numbers. Approximate. | `3.14`, `0.01` | Measuring real-world physics, prices. |

### 2. The Arithmetic Operators
Python provides standard operators for math.

*   `+` (Adition)
*   `-` (Subtraction)
*   `*` (Multiplication)
*   `/` (Division) -> **ALWAYS returns a float**.
*   `**` (Exponentiation) -> Power (e.g., `2 ** 3` is $2^3$).

### 3. The "Viral Float" Rule
The moment a `float` enters a calculation, the entire result becomes a `float`.
*   `int` + `int` = `int`
*   `int` + `float` = `float`

## 🛠️ Syntactic Sugar

### Check your zeros
When writing large numbers, it is easy to lose count of zeros.
*   **Bad**: `salary = 1000000` (Is that a million or 100k?)
*   **Good**: `salary = 1_000_000` (Python ignores underscores in numbers).

## ⚠️ The Floating Point Trap (IEEE 754)
Computers store numbers in **binary** (Base 2). Humans calculate in **decimal** (Base 10).
Some simple decimal fractions (like 0.1) cannot be represented universally in binary, leading to tiny precision errors.

```python
print(0.1 + 0.2)
# Output: 0.30000000000000004
```
*   **Implication**: **NEVER** check if two floats are exactly equal (`if x == 0.3`). They might differ by a microscopic amount.

## 📝 Order of Operations (PEMDAS)
Python follows standard math rules.
1.  **P**arentheses `()`
2.  **E**xponents `**`
3.  **M**ultiplication `*` & **D**ivision `/` (Left to Right)
4.  **A**ddition `+` & **S**ubtraction `-` (Left to Right)

## ⚡ Associations
*   **`/`**: Returns a float (`10 / 2` -> `5.0`).
*   **`**`**: Power/Exponent.
*   **`1_000`**: Underscores usually mean "comma" for humans.

## 🔍 Truth Table

| Expression | Result | Type | Reason |
| :--- | :--- | :--- | :--- |
| `10 + 5` | `15` | `int` | Pure integer math. |
| `10 / 5` | `2.0` | `float` | Division always produces floats. |
| `10 + 2.0` | `12.0` | `float` | Viral float rule. |
| `2 ** 3` | `8` | `int` | $2^3$. |
| `"A" * 3` | `"AAA"` | `str` | String repetition (Not math!). |

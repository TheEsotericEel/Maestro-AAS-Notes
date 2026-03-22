# Lesson 07: Division Modes

## 🎯 End Goal
To master the three flavors of division in Python and understand which one to apply to a given problem.

## 🧠 Core Concepts

### 1. True Division (`/`)
This is the division you learned in science class. It divides numbers as precisely as possible, dealing in fractions/decimals.
*   **Symbol**: The forward slash `/`.
*   **Return Type**: Always a `float`.
*   **Mental Model**: Cutting a cake. You can have 2.5 pieces.

### 2. Floor Division (`//`)
This is the division you learned in 3rd grade (before decimals). It deals in "whole groups."
*   **Symbol**: The double slash `//`.
*   **Return Type**: An `int` (usually).
*   **Mental Model**: Distributing full cartons of eggs. If you have 2.5 cartons, you realistically only have 2 full ones.

### 3. The Remainder (Modulo `%`)
This is the "leftover" from Floor Division.
*   **Symbol**: The percent sign `%` (Read as "Modulo" or "Mod").
*   **Mental Model**: The 50 cents left in your pocket after buying as many $1 sodas as possible.

## 📝 The Division Algorithm (Euclidean Division)
Everything in computer division relies on this mathematical truth:
$$Dividend = (Divisor \times Quotient) + Remainder$$

If we divide `13` by `4`:
*   **Quotient** (`//`): 3 (We can make 3 full groups of 4).
*   **Remainder** (`%`): 1 (There is 1 left over).
*   **Check**: $13 = (4 \times 3) + 1$.

## 🛠️ Practical Use Cases

### Scenario A: Splitting the Bill
You owe money. Precision matters.
```python
bill = 50.00
people = 3
share = bill / people 
print(share) # 16.666666666666668 (Use True Division)
```

### Scenario B: Pagination
You have 105 items. Examples show 10 items per page. How many full pages do you need?
```python
items = 105
per_page = 10
full_pages = items // per_page
print(full_pages) # 10 (Use Floor Division)
```

### Scenario C: Alternating Colors
You want every other row to be gray.
```python
row_number = 5
# If remainder of division by 2 is 0, it's Even. Otherwise, Odd.
is_even = (row_number % 2) == 0 
```

## ⚠️ Traps and Pitfalls

| Mistake | Code | Result | Why? |
| :--- | :--- | :--- | :--- |
| **Negative Floor** | `-5 // 2` | `-3` | Floor means "move left on number line." Left of -2.5 is -3. |
| **Small vs Big** | `2 // 5` | `0` | If you have 2 cookies and need 5 to make a box, you make 0 boxes. |
| **Small vs Big (%)** | `2 % 5` | `2` | If you start with 2 and use none, you have 2 left over. |

## 🔍 Truth Table

| Operation | Concept | Result | Note |
| :--- | :--- | :--- | :--- |
| `13 / 4` | Precise | `3.25` | Float. |
| `13 // 4` | Quotient | `3` | "How many times does 4 fit in 13?" |
| `13 % 4` | Remainder | `1` | "What is left?" |
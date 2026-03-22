# Lesson 08: Modulo in Practice

## 🎯 End Goal
To master the **Modulo Operator** (`%`), moving beyond simple division to robustly handle cycles, parity (even/odd), and pattern detection.

## 🧠 Core Concepts

### 1. Clock Arithmetic (Cyclicity)
The modulo operator calculates the **remainder** of a division. In practice, this creates a "wrapping" effect, just like a clock.
*   **The Rule**: The result of `x % n` will **ALWAYS** be between `0` and `n-1`.
*   **Analogy**: On a 12-hour clock, 13:00 is actually 1:00. Mathematical translation: `13 % 12 = 1`.

### 2. Parity (Even vs. Odd)
Modulo is the standard way to check if a number is even or odd.
*   **Even**: Any number perfectly divisible by 2 (Remainder 0).
*   **Odd**: Any number with a remainder of 1 when divided by 2.

### 3. Digit Extraction
Modulo is a scalpel for numbers. It allows you to slice off specific digits.
*   `x % 10`: Returns the last digit. (e.g., `123 % 10` -> `3`).
*   `x % 100`: Returns the last two digits.

## 🛠️ Practical Patterns

### Pattern A: The Toggle (Even/Odd)
Use this to alternate colors in a grid (Striping).
```python
row_number = 5
if row_number % 2 == 0:
    color = "White"
else:
    color = "Gray"
```

### Pattern B: The Carousel (Cyclical Indexing)
You have a list of 3 players. You want to cycle through them indefinitely.
```python
# Players: 0, 1, 2
turn = 0
current_player = turn % 3 # Result: 0

turn = 1
current_player = turn % 3 # Result: 1

turn = 2
current_player = turn % 3 # Result: 2

turn = 3
current_player = turn % 3 # Result: 0 (Wraps back to start!)
```

### Pattern C: The "Every Nth" Item
Use this to trigger an event every 100 frames or 10th item.
```python
count = 500
if count % 100 == 0:
    print("Checkpoint reached!")
```

## ⚡ Associations
*   **`% 2 == 0`** -> Even.
*   **`% 2 == 1`** -> Odd.
*   **`% 10`** -> Get last digit.
*   **`0` to `N-1`** -> The range of possible results.

## ⚠️ Traps and Pitfalls

| Mistake | Code | Result | Why? |
| :--- | :--- | :--- | :--- |
| **Modulo by Zero** | `10 % 0` | `ZeroDivisionError` | You cannot have a remainder if you can't divide. |
| **Thinking it's Division** | `10 % 5` | `0` | Beginner thinks "10 divided by 5 is 2". No! % asks for the *leftover*. There is none. |
| **Float Modulo** | `5.5 % 2` | `1.5` | Python allows float modulo, but it is rare and prone to precision errors. |

## 🔍 Truth Table

| Expression | Result | Implementation | logic |
| :--- | :--- | :--- | :--- |
| `10 % 3` | `1` | `10 // 3 = 3`. $10 - (3 \times 3) = 1$ | $10 = 3 \times 3 + 1$ |
| `11 % 3` | `2` | `11 // 3 = 3`. $11 - (3 \times 3) = 2$ | $11 = 3 \times 3 + 2$ |
| `12 % 3` | `0` | `12 // 3 = 4`. $12 - (4 \times 3) = 0$ | $12 = 3 \times 4 + 0$ |

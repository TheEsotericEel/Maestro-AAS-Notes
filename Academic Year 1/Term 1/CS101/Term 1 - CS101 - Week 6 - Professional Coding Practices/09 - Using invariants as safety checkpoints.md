# Lesson 09: Using Invariants as Safety Checkpoints

## 1. The Core Philosophy
> "Fail Fast. Fail Loud."

In Software Engineering, a **Silent Failure** (processing bad data without crashing) is infinitely worse than a **Crash**. A crash gets fixed. A silent failure corrupts your database for years.

## 2. Theoretical Framework: Design by Contract
Proposed by Bertrand Meyer, this concept treats functions as contracts.
*   **Pre-conditions**: What must be true *before* the function runs.
*   **Post-conditions**: What must be true *after* the function runs.
*   **Invariants**: What must be true *always* (during the execution).

## 3. The `assert` Statement
Python provides the `assert` keyword to enforce these contracts.
Syntax: `assert condition, "Error Message"`
*   If `condition` is `True`: Nothing happens.
*   If `condition` is `False`: The program crashes immediately with `AssertionError`.

## 4. Practical Implementation

### Defensive Programming
We rely on assertions to catch **Programmer Logic Errors** (mistakes in the code), not **Runtime Errors** (mistakes by the user).

**Example: The Discount Calculator**
```python
def apply_discount(price: float, discount_percent: float) -> float:
    # Pre-condition: Price cannot be negative
    assert price >= 0, f"Invariant Violation: Price is negative ({price})"
    
    # Pre-condition: Discount must be between 0 and 1
    assert 0 <= discount_percent <= 1, f"Invariant Violation: Invalid discount ({discount_percent})"

    # The Logic
    final_price = price * (1 - discount_percent)

    # Post-condition: Discounted price must be <= original price
    assert final_price <= price, "Invariant Violation: Discount made price higher!"
    
    return final_price
```

## 5. When NOT to use Assert
**Do not** use `assert` for user input validation.
*   **Why?** In optimized Python (`python -O`), assertion checks are **removed** for performance.
*   **Rule**: Use `assert` for things that should *never* happen if the code is correct. Use `if/raise ValueError` for things that *might* happen (like bad user input).

| Scenario | Tool |
| :--- | :--- |
| User enters "Bob" instead of number | `if/raise` (Validation) |
| Function receives -5 as age | `assert` (Logic Error - caller is buggy) |
| Database is unreachable | `try/except` (Runtime Error) |

## 6. Summary
Invariants are your safety nets. They ensure that if your code logic is flawed, the program stops before it can do any damage.

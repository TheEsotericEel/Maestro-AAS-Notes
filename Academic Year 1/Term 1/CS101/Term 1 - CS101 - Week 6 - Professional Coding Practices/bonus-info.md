# Week 6 Reference Guide: Professional Coding Practices

> **"Code is read much more often than it is written."** — Guido van Rossum

## 1. Naming Conventions (The Laws)
We follow **PEP 8**.

| Type | Convention | Example |
| :--- | :--- | :--- |
| **Variable** | `snake_case` | `user_count`, `is_valid` |
| **Function** | `snake_case` | `calculate_total()`, `fetch_user()` |
| **Class** | `PascalCase` | `UserProfile`, `GameManager` |
| **Constant** | `SCREAMING_SNAKE` | `MAX_RETRIES`, `DEFAULT_COLOR` |

### The Telephone Test
Read your variable name aloud. If you have to explain it, rename it.
*   *Fail*: `d` ("The dictionary").
*   *Pass*: `inventory_map`.

## 2. Docstrings (The Contract)
Write docstrings for every function. Use the Google Style logic.

```python
def function_name(param1: type, param2: type) -> return_type:
    """Imperative summary of what the function does.

    More detailed explanation if necessary.

    Args:
        param1: Description.
        param2: Description.

    Returns:
        Description of return value.
    
    Raises:
        ValueError: If param1 is invalid.
    """
    pass
```

## 3. Code Structure (The Newspaper)
Structure code to minimize cognitive load.
1.  **Imports**: Standard lib first, then third party, then local.
2.  **Constants**: Configurations at the top.
3.  **Core Functions**: The important business logic.
4.  **Helpers**: The low-level details at the bottom.
5.  **Main Entry**: `if __name__ == "__main__":` block.

## 4. Defensive Programming (The Fortress)
*   **Guard Clauses**: Check for invalid input immediately and return/raise. Avoid nesting.
*   **Invariants**: Use `assert` to catch impossible states (Programmer Errors).
*   **Exceptions**: Use `raise ValueError` or `TypeError` for clear feedback (User/Input Errors).

## 5. Refactoring Patterns
*   **Extract Function**: Move a block of code into a named function (`process_payment()`).
*   **Extract Variable**: Move a magic number or complex boolean into a named variable (`is_eligible`).
*   **Early Return**: Convert nested `if`s into a flat list of Guard Clauses.

## 6. Debugging Protocol
1.  **Reproduce**: Script the failure.
2.  **Isolate**: Find the function.
3.  **Trace**: Use `print(f"[DEBUG] var={var}")` to verify state.
4.  **Fix**: Apply change.
5.  **Verify**: Run reproduction script.

## 7. Testing Strategy
*   **Happy Path**: Does it work when everything is correct?
*   **Edge Cases**: 0, Empty, Negative, Max+1.
*   **Table-Driven Tests**: Loop over a list of scenarios.

## 8. Glossary
*   **Cognitive Load**: The mental effort required to understand code.
*   **Cohesion**: How closely related the parts of a function are (Goal: High).
*   **Coupling**: How dependent a function is on the rest of the system (Goal: Low).
*   **Idempotent**: A function that can be called multiple times without changing the result beyond the initial application.
*   **Pure Function**: A function with no side effects (Input -> Output only).

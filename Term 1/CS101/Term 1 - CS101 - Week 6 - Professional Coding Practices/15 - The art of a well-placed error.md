# Lesson 15: The Art of a Well-Placed Error

## 1. The Core Philosophy
An error message is an API. It is a communication channel from the system to the developer.
*   **Bad Error**: "Something went wrong." (The system is confused).
*   **Good Error**: "I cannot calculate the square root of -1." (The system is precise).

## 2. Theoretical Framework: Exception Hierarchy
Python has a taxonomy of errors. Use the right Latin names for your bugs.
*   `TypeError`: The code expected a Cat and got a Dog. (`add(5, "5")`).
*   `ValueError`: The code expected a Positive Number and got a Negative one. (`sqrt(-1)`).
*   `RuntimeError`: The code is fine, but the world is broken (Disk full, Network down).

## 3. The Anatomy of a Helpful Error
A professional error message contains three components:
1.  **The Context**: What were we trying to do?
2.  **The Offender**: What value caused the failure?
3.  **The Constraint**: Why is that value bad?

**Bad**:
```python
raise ValueError("Invalid Input")
```

**Professional**:
```python
raise ValueError(f"Cannot set age to {age}. Age must be between 0 and 120.")
```

## 4. The "Check-Raise" Pattern
Don't wait for your library calls to crash. Crash the program yourself, on your terms.

**Lazy (Letting it crash):**
```python
def get_user(id):
    # If id is None, this crashes with a confusing "AttributeError" deep inside the DB driver.
    return db.query(id) 
```

**Proactive (Raising):**
```python
def get_user(id):
    if id is None:
        raise ValueError("User ID cannot be None.")
    return db.query(id)
```

## 5. Summary
A crash is better than a silent failure. A *clear* crash is better than a *cryptic* crash. Be the friendly waiter who explains exactly why the kitchen cannot serve the soup.

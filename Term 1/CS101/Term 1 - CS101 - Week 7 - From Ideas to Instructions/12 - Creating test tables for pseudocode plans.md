# Test-Driven Logic Design

## 1. The Engineering Truth Table

### What is it?
A Truth Table (or Test Table) is a matrix that maps every possible category of **Input** to a strictly defined **Expected Output**.

### Why does it matter?
You cannot write code to solve a problem if you don't know what the solution looks like. The table forces you to make decisions about edge cases *before* you are trapped in Python syntax.

### The Standard Format
| Case Type | Input Variables | Expected Output | Logic/Reason |
| :--- | :--- | :--- | :--- |
| **Normal** | 50 | Pass | Score > 40 |
| **Normal** | 30 | Fail | Score < 40 |
| **Boundary** | 40 | Pass | Score >= 40 (Inclusive) |
| **Invalid** | -5 | Error | Cannot be negative |

---

## 2. Test Coverage Theory

To prove logic is sound, you must test three domains:

1.  **The Happy Path**: Standard, expected inputs. (e.g., Age 25).
2.  **The Edge Cases**: The exact boundaries of logic gates. (e.g., Age 18, Age 21). Logic errors usually hide here.
3.  **The Failure Modes**: Invalid or unexpected data. (e.g., Age -1, Age "Ten").

---

## 3. Practical Example: The Leap Year

**Rule**:
*   Divisible by 4? Yes.
*   Unless divisible by 100? No.
*   Unless divisible by 400? Yes.

**The Test Table**
| Year | Expected | Reason |
| :--- | :--- | :--- |
| 2024 | **True** | Div by 4, not 100. (Normal Leap) |
| 2023 | **False** | Not div by 4. (Normal Non-Leap) |
| 1900 | **False** | Div by 100, but not 400. (Century Exception) |
| 2000 | **True** | Div by 400. (Quarter-Century Exception) |

**Verification Code**
```python
test_cases = [
    (2024, True),
    (2023, False),
    (1900, False),
    (2000, True)
]

for year, expected in test_cases:
    result = is_leap_year(year)
    if result != expected:
        print(f"BUG! Year {year}: Expected {expected}, Got {result}")
    else:
        print(f"PASS: {year}")
```
*If this code runs silent, your logic is perfect.*

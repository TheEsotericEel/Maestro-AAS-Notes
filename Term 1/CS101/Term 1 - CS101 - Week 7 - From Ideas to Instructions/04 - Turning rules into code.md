# Implementing Boolean Logic and Conditionals

## 1. Boolean Logic: The Traffic Cop

### What is it?
Boolean logic determines the path a program takes. It is binary: a condition is either `True` or `False`. There is no "maybe."

### The "If-Elif-Else" Ladder
This structure ensures that **mutually exclusive** conditions are handled correctly.
*   **IF**: The first check.
*   **ELIF** (Else If): Only checked if the previous `IF` (and `ELIF`s) were `False`.
*   **ELSE**: The catch-all. If nothing above matched, this runs.

### Why does it matter?
Without this structure, programs would execute every single line of code, regardless of context. Logic gates allow softare to react dynamically to input.

---

## 2. Boolean Algebra

### Operators
| Operator | Meaning | Example | Result |
| :--- | :--- | :--- | :--- |
| `==` | Equality | `5 == 5` | `True` |
| `!=` | Inequality | `5 != 3` | `True` |
| `>` | Greater Than | `10 > 2` | `True` |
| `<` | Less Than | `1 < 0` | `False` |

### Logical Connectors
| Connector | Usage | Truth Table |
| :--- | :--- | :--- |
| **AND** | `A and B` | True only if **BOTH** are true. |
| **OR** | `A or B` | True if **AT LEAST ONE** is true. |
| **NOT** | `not A` | Inverts the value. |

---

## 3. Practical Examples

### Example 1: The Grading System (Mutually Exclusive)
**Task**: Assign a grade based on a score.
*   90+ = A
*   80-89 = B
*   70-79 = C
*   Below 70 = F

**Correct Logic (The Ladder)**
```python
def get_grade(score):
    if score >= 90:
        return "A"
    elif score >= 80:
        # We don't need to check check "score < 90" 
        # because the first IF already caught those cases!
        return "B"
    elif score >= 70:
        return "C"
    else:
        # Catch-all for everything else (0-69)
        return "F"
```

**Common Mistake (The Gap)**
```python
# BUGGY CODE
if score > 90:
    return "A"
if score > 80:    # If score is 95, this ALSO runs!
    return "B"    # Student gets "B" overwriting "A" logic? 
                  # Or returns multiple times? Ambiguous.
```

### Example 2: Complex Access Control (AND/OR)
**Task**: Allow access if user is an Admin OR (User is active AND has permission).

**Pseudocode**
```text
IF role == "admin":
    Access Granted
ELSE IF status == "active" AND permission == "read":
    Access Granted
ELSE:
    Access Denied
```

**Python Implementation**
```python
def check_access(user):
    is_admin = user.role == 'admin'
    is_active_user = user.status == 'active'
    has_permission = 'read' in user.permissions
    
    # Combined Logic
    if is_admin or (is_active_user and has_permission):
        return True
    
    return False
```

## 4. Edge Case Handling

Always ask: **"What about the zero? What about the negative? What about the empty string?"**

*   **The Zero**: If dividing, `x / 0` crashes. Guard against it.
*   **The Negative**: Can age be `-5`? If implementation uses `<= 13`, `-5` is treated as a child. Validation required.
*   **The Type**: Is the input actually a number?

**Robust Logic Example:**
```python
def calculate_price(age):
    if not isinstance(age, int):
        return "Error: Invalid Input"
        
    if age < 0:
        return "Error: Age cannot be negative"
        
    if age < 18:
        return 10
    else:
        return 20
```

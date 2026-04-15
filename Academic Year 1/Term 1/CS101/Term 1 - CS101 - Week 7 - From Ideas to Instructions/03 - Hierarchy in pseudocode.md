# Control Structures and Scope Hierarchy

> "Structure is strict code's best friend."

## 1. Scope and Indentation

### What is it?
**Scope** defines the lifespan and visibility of variables and logic. In visual terms, it is the "container" that code lives within.
**Indentation** is the visual representation of scope. In many languages (C++, Java), scope is defined by curly braces `{}`. In Python and Pseudocode, scope is defined by **whitespace** (indentation).

### Why does it matter?
Indentation determines *ownership*. A line of code indented under an `IF` statement belongs to that condition. It will *only* execute if that condition is true. Misaligned indentation is the #1 cause of logic errors in Python.

### The Hierarchy
1.  **Parent** (The Controller): The loop or condition.
2.  **Child** (The Worker): The code that runs *inside* the parent.
3.  **Grandchild**: Code nested inside a child logic block.

---

## 2. Control Flow Structures

There are two main "Parents" in programming:

### A. Repetition (Loops)
"Do this X times" or "Do this for every item."
*   **Keyword**: `FOR`, `WHILE`.
*   **Behavior**: The indented block repeats.

### B. Selection (Conditionals)
"Do this ONLY IF X is true."
*   **Keyword**: `IF`, `ELSE`.
*   **Behavior**: The indented block executes 0 or 1 time.

---

## 3. Practical Examples

### Example 1: The "Scope Check"
**Task**: Send an email to premium users.

**Incorrect Structure (Flat)**
```text
FOR each user in users:
IF user is premium:
Send Email                 <-- AMBIGUOUS. Is this inside the IF?
Update Database            <-- AMBIGUOUS. Is this inside the LOOP?
```

**Correct Structure (Hierarchical)**
```text
1. FOR each user in users:        # Parent (Loop)
    1.1 Check stats               # Child (Runs for every user)
    
    1.2 IF user is premium:       # Child (Condition)
        1.2.1 Send Email          # Grandchild (Runs ONLY if premium)
        1.2.2 Log Success         # Grandchild
        
    1.3 Update Database           # Child (Runs for every user, after IF check)
```

### Example 2: Complex Nesting (The Matrix)
**Task**: Find the first even number in a matrix (list of lists).

```python
matrix = [
    [1, 3, 5],
    [7, 8, 9],  # 8 is the target
    [10, 11, 12]
]
```

**Pseudocode Plan**
```text
FUNCTION FindFirstEven(matrix):
    FOR each row in matrix:                # Level 1
        Print "Checking row..."
        
        FOR each number in row:            # Level 2 (Nested Loop)
            
            IF number is even:             # Level 3 (Condition)
                RETURN number              # Stop everything and return
                
            Print "Odd found, skipping"    # Level 2 Logic
            
    RETURN "No even numbers found"         # Level 0 (Backup return)
```

### Visualizing Execution
1.  **Level 1**: We enter Row 1 `[1, 3, 5]`.
2.  **Level 2**: We iterate 1, then 3, then 5.
3.  **Level 3**: The `IF` is never true.
4.  **Level 1**: We enter Row 2 `[7, 8, 9]`.
5.  **Level 2**: We check 7.
6.  **Level 2**: We check 8.
7.  **Level 3**: `IF` is true! We `RETURN 8`.
8.  **Exit**: The program ends immediately. The code never sees `9` or Row 3.

# Decomposition and Sequential Logic

> "If you can't explain it simply, you don't understand it well enough."  
> — *Albert Einstein*

## 1. The Art of Decomposition

### What is it?
Decomposition is the process of breaking a complex system down into smaller, manageable parts. In computer science, this means taking a vague request (e.g., "Build a calculator") and breaking it down into atomic, executable steps (e.g., "Get input A", "Get input B", "Add A and B", "Display Result").

### Why does it matter?
Computers are **deterministic machines**. They do not possess intuition. A command like "clean the data" is meaningless to a computer. You must specify *how* to clean it: "Remove rows where column A is null" or "Trim whitespace from column B". Decomposition bridges the gap between human intent and machine execution.

### Who uses it?
Every engineer, from junior developers to system architects. It is the fundamental skill of the profession.

---

## 2. The IPO Model

All algorithms, no matter how complex, follow the **IPO** structure.

| Phase | Definition | Examples |
| :--- | :--- | :--- |
| **Input** | Gathering raw data from an external source. | `input()`, `read_file()`, API response, database query. |
| **Process** | Transforming data using logic and math. | `sum()`, `filter()`, `if/else`, sorting, formatting. |
| **Output** | Delivering the result to a destination. | `print()`, `save_file()`, sending an email, updating a UI. |

### The IPO Check
If your pseudocode line doesn't fit into one of these buckets, it is likely vague or invalid.
*   *Bad*: "Manage the user." (Vague).
*   *Good*: "Ask user for name (Input)." -> "Capitalize name (Process)." -> "Save to DB (Output)."

---

## 3. Deterministic Execution (The Robot Mindset)

When writing pseudocode, assume you are programming a robot with zero common sense.

### The "Robot Protocol"
1.  **Sequential Execution**: The robot performs step 1, then step 2, then step 3. It never jumps ahead unless told to.
2.  **Literal Interpretation**: If you say "Drop the ball," it drops it. It does not check if exactly one ball is in hand.
3.  **No Assumptions**: It does not know that "Enter age" implies a number. You must tell it to "Validate that input is a number."

---

## 4. Practical Examples

### Example 1: The Iterative Refinement
**Task**: "Calculate the average score."

**Draft 1 (Too Vague - Human Level)**
```text
1. Get the numbers
2. Calculate average
3. Print it
```

**Draft 2 (Better - Logical Level)**
```text
1. Create a list of scores: [80, 90, 100]
2. Add them all up
3. Divide by the number of scores
4. Print result
```

**Draft 3 (Gold Standard - Atomic Level)**
```text
PROGRAM CalculateAverage:
    # INPUT
    DECLARE scores = [80, 90, 100]
    
    # PROCESS
    DECLARE total = 0
    FOR each score in scores:
        total = total + score
        
    DECLARE count = length of scores
    DECLARE average = total / count
    
    # OUTPUT
    PRINT average
END
```

### Example 2: Real-World Data Processing
**Task**: processing a CSV file of users.

```text
PROGRAM ProcessUsers:
    # INPUT
    Open "users.csv"
    Read all lines into `raw_data`
    
    # PROCESS
    Initialize `valid_users` list
    
    FOR each line in `raw_data`:
        Split line by comma
        Extract `email` and `age`
        
        # Validation Logic
        IF `email` contains "@" AND `age` > 18:
            Add user to `valid_users`
            
    # OUTPUT
    Open "clean_users.csv"
    Write headers
    FOR each user in `valid_users`:
        Write user to file
END
```

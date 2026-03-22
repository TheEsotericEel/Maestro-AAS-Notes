# System Integration and Data Flow

## 1. The Supervisor Pattern

### What is it?
Integration is the phase where individual, tested components (functions) are assembled into a working machine.
The **Supervisor Pattern** dictates that a single `main()` function should coordinate the flow of data between these components.

### Why does it matter?
Without a Supervisor, functions become tightly coupled (Function A calls Function B directly). This makes testing impossible.
*   **Bad**: `get_input()` calls `calculate()`.
*   **Good**: `main()` calls `get_input()`, stores the result, and *then* passes it to `calculate()`.

---

## 2. The Data Pipeline

Visualizing your application as a factory line:
1.  **Raw Material** (User Input).
2.  **Quality Control** (Validation).
3.  **Manufacturing** (Logic/Math).
4.  **Packaging** (Formatting).
5.  **Shipping** (Print/Output).

**The Handoff Contract**:
If Station 2 expects an `Integer` but Station 1 passes a `String`, the machine jams. You must ensure data types remain consistent across handoffs.

---

## 3. Practical Example: The Loan Calculator

**The Components (Built Incrementally)**
```python
def get_income():
    return float(input("Income: "))

def calculate_limit(income):
    return income * 3.5

def check_eligibility(income):
    return income > 20000

def display_result(limit):
    print(f"Approved. Limit: ${limit}")
```

**The Integration (The Main Logic)**
```python
def main():
    # 1. Input
    inc = get_income()
    
    # 2. Logic Branch
    if check_eligibility(inc):
        # 3. Calculation
        limit = calculate_limit(inc)
        
        # 4. Output
        display_result(limit)
    else:
        # Error Path
        print("Loan Denied: Income too low.")

# The Switch
if __name__ == "__main__":
    main()
```

### Integration Tips
1.  **Fail Fast**: Check for errors (Eligibility) as early as possible.
2.  **Pass Data, Not Globals**: Never use global variables. Pass `inc` into `calculate_limit(inc)`.
3.  **Debug the Gap**: If `limit` is wrong, print `inc` right before the function call to ensure the input was correct.

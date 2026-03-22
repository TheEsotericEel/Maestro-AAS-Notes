# Breaking Down a Case Study

## 1. Concept: Functional Core, Imperative Shell
> **Definition**: An architectural pattern popularized by **Gary Bernhardt**. It strictly separates code that **Does** things (I/O, Side Effects) from code that **Thinks** (Pure Logic).

*   **The Shell (Imperative)**: Reads files, talks to DBs, prints to screen. (Talking).
*   **The Core (Functional)**: Transforms data, makes decisions, calculates. (Thinking).

## 2. The "Why": The Boundary of Risk
*   **Logic** is safe, fast, and deterministic. `1 + 1` always equals `2`.
*   **I/O** is risky, slow, and random. The network might fail. The file might be missing.
*   By pushing I/O to the edges (The Shell), we create a safe haven for our logic (The Core) where testing is easy.

## 3. The "How": The Sandwich Method
Structure your process like a sandwich:
1.  **Top Bun (Input/I/O)**: Gather all necessary data *first*.
2.  **Meat (Process/Logic)**: Do all calculations in memory. No DB calls here.
3.  **Bottom Bun (Output/I/O)**: Save or display the results *last*.

## 4. Case Study: The Order Processor

### The Problem
"Read a list of orders from a CSV, calculate the total revenue for 'Pending' orders, and email the manager."

### Step 1: Decomposition (The Organs)
1.  `read_csv(filename)` -> List of Dicts (Input).
2.  `filter_pending(orders)` -> List of Dicts (Logic).
3.  `sum_revenue(orders)` -> Float (Logic).
4.  `send_email(total)` -> None (Output).

### Step 2: The Scaffold (The Skeleton)
Before writing logic, write the flow:
```python
def main():
    # 1. Talking
    orders = read_csv("orders.csv")

    # 2. Thinking
    pending = filter_pending(orders)
    total = sum_revenue(pending)

    # 3. Talking
    send_email(total)
```

### Step 3: Implementation (The Meat)
Now implement the pure functions.
```python
def filter_pending(orders):
    # Pure logic. No CSV reading here.
    return [o for o in orders if o['status'] == 'Pending']

def sum_revenue(orders):
    # Pure logic. No email sending here.
    return sum(o['amount'] for o in orders)
```

## 5. Truth: Plan in English, Execute in Python
If you cannot explain the flow in three English sentences (Input, Process, Output), you are not ready to write code.
*   **Bad**: "I'll loop through the file and checking the DB..." (Mixing steps).
*   **Good**: "First, I'll load the data. Second, I'll filter for X. Third, I'll save."

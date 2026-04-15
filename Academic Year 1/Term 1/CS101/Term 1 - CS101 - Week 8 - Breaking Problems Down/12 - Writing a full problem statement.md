# Writing a Full Problem Statement

## 1. Concept: Specification Engineering
> **Definition**: A Problem Statement (or Spec) is the rigorous, unambiguous definition of a software solution. It combines **Purpose**, **Constraints** (Inputs), and **Success Criteria** (Outputs) into a single source of truth.

In professional engineering, "The Spec" is the contract. If code meets the spec but fails the user, the spec was wrong. If code fails the spec, the code is wrong.

## 2. The "Why": The Cost of Ambiguity
Correcting a misunderstanding during the **Spec Phase** costs \$1.
Correcting it during the **Code Phase** costs \$10.
Correcting it after **Deployment** costs \$100.

Writing a full problem statement is the cheapest way to debug your code.

## 3. The "How": The "IOS-C" Template
A complete statement must contain:
1.  **I**nputs: Data types, ranges, nullability.
2.  **O**utputs: Return types, error states.
3.  **S**uccess Criteria: Exact input/output pairs (Test Cases).
4.  **C**onstraints: Performance limits, forbidden libraries, hardware limits.

## 4. Example: The Library Fine Calculator

### The Request
"Write a thing to calculate fines for late books."

### The Problem Statement (The Constitution)

#### 1. Purpose
Calculate the monetary fine for a library book based on days overdue and book status.

#### 2. Inputs (The Contract)
*   `days_overdue`: Integer. Must be >= 0.
*   `is_lost`: Boolean. True if the book is declared lost.

#### 3. Outputs
*   `fine_amount`: Float. Rounded to 2 decimal places.

#### 4. Logic & Rules (The Law)
1.  **Base Rate**: $0.25 per day.
2.  **Cap**: The maximum fine for a returned book is $5.00.
3.  **Lost Penalty**: If the book is lost, the fine is $25.00 flat (ignoring days).
4.  **Grace Period**: First 2 days are free.

#### 5. Success Criteria (Test Plan)
| Case | Input (Days / Lost) | Expected Output | Rule Applied |
| :--- | :--- | :--- | :--- |
| **Grace** | `1`, `False` | `$0.00` | Grace Period. |
| **Standard** | `10`, `False` | `$2.00` | (10-2) * 0.25. |
| **Capped** | `100`, `False` | `$5.00` | Max Cap. |
| **Lost** | `5`, `True` | `$25.00` | Lost Penalty overrides Cap. |

## 5. From Spec to Code
Once the "IOS-C" is written, the code writes itself.

```python
def calculate_fine(days_overdue: int, is_lost: bool) -> float:
    # Rule 3: Lost Penalty
    if is_lost:
        return 25.00
    
    # Rule 4: Grace Period
    effective_days = max(0, days_overdue - 2)
    
    # Rule 1: Base Rate
    fine = effective_days * 0.25
    
    # Rule 2: Cap
    return min(fine, 5.00)
```

## 6. Truth: The Spec is the Map
Code is just the vehicle. The Spec is the destination.
If you start driving (coding) without a destination (spec), you will drive fast, but you will not arrive.

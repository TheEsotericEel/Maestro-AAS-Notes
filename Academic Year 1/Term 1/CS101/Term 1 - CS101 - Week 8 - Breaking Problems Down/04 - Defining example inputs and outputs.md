# Defining Example Inputs and Outputs

## 1. Concept: Test-Driven Thinking
> **Definition**: The practice of defining concrete `(Input, Expected Output)` pairs **before** writing implementation logic. This aligns with **Test-Driven Development (TDD)** principles.

This is the scientific method applied to coding: Establish a hypothesis (Input X should yield Output Y), then build the experiment (Code) to confirm it.

## 2. The "Why": Validation vs. Verification
Why do we define examples first?
1.  **Ambiguity Resolution**: "Handle bad input" is vague. `Input: -1 -> Output: Error` is precise.
2.  **Regression Safety**: These examples become your automated test suite, ensuring future changes don't break existing functionality.
3.  **Correctness**: You cannot know if your code works if you don't know what "work" looks like.

## 3. The "How": Partitioning the Domain
To fully cover a problem space, you must select examples from three specific sets:

### 1. Happy Path (Standard Usage)
Inputs that represent the normal, expected operation of the software.
*   *Example*: A login with correct username and password.

### 2. Edge Cases (Boundaries)
Inputs at the exact "edges" of logic logic. Errors most frequently occur here (Off-by-one errors).
*   *Example*: A bank transfer of $0.00. A list with 1 item. A string with max allowed length.

### 3. Error Cases (Invalid Input)
Inputs that should be rejected or handled gracefully.
*   *Example*: A negative age. A null string. A SQL injection attempt.

## 4. Examples: Designing the Test Suite

### The Grade Calculator
**Logic**: 90-100 is A, 80-89 is B, <80 is F.

| Category | Input (Score) | Expected Output | Rationale |
| :--- | :--- | :--- | :--- |
| **Happy** | `95` | `"A"` | Standard A. |
| **Happy** | `85` | `"B"` | Standard B. |
| **Edge** | `90` | `"A"` | Lower bound of A. Exclusive or Inclusive? |
| **Edge** | `89` | `"B"` | Upper bound of B. |
| **Edge** | `0` | `"F"` | Minimum valid score. |
| **Error** | `-1` | `ValueError` | Scores cannot be negative. |
| **Error** | `105` | `ValueError` | Scores cannot exceed 100. |

### The "Zero-One-Many" Heuristic
When testing collections (lists, arrays), always test:
1.  **Zero**: Empty list `[]`.
2.  **One**: Single item `[x]`.
3.  **Many**: Multiple items `[x, y, z...]`.

## 5. Implementation: Parameterized Tests
In modern testing frameworks (like `pytest`), we represent this directly in code:

```python
import pytest

# Define the data table
@pytest.mark.parametrize("input_score, expected_grade", [
    (95, "A"),  # Happy
    (90, "A"),  # Edge
    (89, "B"),  # Edge
    (70, "F"),  # Happy
])
def test_grading_logic(input_score, expected_grade):
    assert calculate_grade(input_score) == expected_grade

def test_invalid_scores():
    with pytest.raises(ValueError):
        calculate_grade(-1)
```

## 6. Truth: The Map is Not the Territory
Your logic is the **Territory** (complex, abstract).
Your examples are the **Map** (concrete, pinned points).
If the map is wrong, you *will* get lost in the territory.

# Lesson 12: Stress It to the Edge

## 1. The Core Philosophy
Amateur code works when everything goes right (The "Happy Path").
Professional code works when everything goes wrong.

## 2. Theoretical Framework: Equivalence Partitioning
You cannot test every possible number. You group them into sets that behave similarly.
*   **Valid Set**: 1 to 100. (Test one number, e.g., 50).
*   **Invalid Low**: < 1. (Test 0 and -1).
*   **Invalid High**: > 100. (Test 101 and 1000).

## 3. Table-Driven Testing
Writing explicit `assert` statements for every case is tedious and prone to error. Use **Table-Driven Tests** to separate data from logic.

### The Problem (`assert` spam)
```python
assert is_adult(18) == True
assert is_adult(20) == True
assert is_adult(17) == False
# Hard to read, hard to maintain.
```

### The Solution (Test Table)
```python
def is_adult(age: int) -> bool:
    return age >= 18

# Define the scenarios
test_cases = [
    # (Input, Expected Result, Description)
    (20, True, "Typical Adult"),
    (18, True, "Boundary Adult"),
    (17, False, "Boundary Minor"),
    (0, False, "Newborn"),
    (-1, False, "Negative Age (Impossible)"),
]

# The Test Runner
for age, expected, desc in test_cases:
    result = is_adult(age)
    if result != expected:
        print(f"❌ FAILED: {desc}. Input: {age}, Wanted: {expected}, Got: {result}")
    else:
        print(f"✅ PASSED: {desc}")
```

## 4. The "Zero, One, Many" Rule
When testing collections (lists, strings), always test:
1.  **Zero**: Empty list `[]`. Does it crash?
2.  **One**: Single item `[x]`. Does the loop logic hold?
3.  **Many**: Multiple items `[x, y, z]`. Does the accumulator work?

## 5. Summary
Your code is a bridge. Driving a lightweight car over it proves nothing. Drive a tank over it. Then drive a feather over it.

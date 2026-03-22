# Defining Subproblem Inputs and Outputs

## 1. Concept: Interface Design
> **Definition**: Defining the boundary between two subproblems. This is a contract that dictates what data passes across the boundary (Arguments) and what data returns (Return Values).

In strictly typed languages (like Java or TypeScript), this is called the **Method Signature**. In dynamic languages (Python, JavaScript), it is often implicit, which makes rigorous documentation even more critical.

## 2. The "Why": The Integration Guarantee
Most software fails at the "seams"—where two parts connect.
*   Module A expects a `Date` object.
*   Module B sends a `String` date ("2023-01-01").
*   **Result**: Crash at runtime.

By defining I/O upfront, we ensure the "key" fits the "lock" before we manufacture them.

## 3. The "How": The Data Contract
For every subproblem, strictly define:
1.  **Inputs (Args)**: Type, Constraints, and Nullability.
2.  **Outputs (Returns)**: Type and Error conditions.

### Handling "Nothing"
Explicitly decide how to handle failure/absence.
*   Return `None`?
*   Raise an `Exception`?
*   Return an empty list `[]`?
*   Return a boolean `False`?
*   **Rule**: Be consistent. Do not return `None` sometimes and `False` other times.

## 4. Examples: Strong vs. Weak Contracts

### Scenario: Finding a User by ID
**❌ Weak Contract (Implicit)**
```python
def find_user(id):
    # What is ID? Int? String?
    # What does it return if found? Dict? Object?
    # What does it return if NOT found? None? Error?
    pass
```

**✅ Strong Contract (Explicit)**
```python
def find_user(user_id: int) -> Optional[User]:
    """
    Input: user_id (Must be positive integer)
    Output: User object if found, None if not found.
    Raises: ValueError if user_id is negative.
    """
    pass
```

### Scenario: The Pipeline "Handshake"
**Step 1**: `get_raw_data()` -> returns `List[String]`
**Step 2**: `clean_data(input)` -> expects `List[String]`
*   **Status**: **Compatible**. The output of 1 matches the input of 2.

**Step 1**: `fetch_coordinates()` -> returns `(float, float)`
**Step 2**: `plot_point(point)` -> expects `Dict{x: float, y: float}`
*   **Status**: **Broken**. Tuple vs Dictionary mismatch.
*   **Fix**: Either change Step 1 to return a Dict, or Step 2 to accept a Tuple.

## 5. Truth: Garbage In, Garbage Out
If you do not define your inputs, your function will accept garbage.
If you accept garbage, you will produce garbage (or crash).
Strict interfaces act as the "Security Guards" of your functions.

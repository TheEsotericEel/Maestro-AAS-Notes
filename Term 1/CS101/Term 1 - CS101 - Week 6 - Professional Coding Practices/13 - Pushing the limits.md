# Lesson 13: Pushing the Limits (Boundary Analysis)

## 1. The Core Philosophy
Most bugs do not live in the middle of the logic. They live at the edges.
*   **Off-by-one errors**: Looping `range(n)` vs `range(n+1)`.
*   **Fencepost errors**: Connecting N posts requires N-1 wires.

## 2. Theoretical Framework: Boundary Value Analysis
If a system accepts values between `1` and `100`, the most critical tests are:
*   **Min**: 1 (Valid)
*   **Min - 1**: 0 (Invalid)
*   **Max**: 100 (Valid)
*   **Max + 1**: 101 (Invalid)

Testing `50` tells you almost nothing. Testing `100` and `101` tells you everything.

## 3. The Cliff Edge Metaphor
Imagine a cliff.
*   **Safe Zone**: Fields far from the edge.
*   **The Edge**: The exact point where the ground ends.
*   **The Fall**: The space immediately after the edge.

### Code Example
```python
def get_letter_grade(score: int) -> str:
    # Boundary: 90 is an A. 89 is a B.
    if score >= 90:
        return 'A'
    if score >= 80:
        return 'B'
    return 'F'
```
*   **Test 90**: Should be 'A'. (On the line).
*   **Test 89**: Should be 'B'. (Just below the line).
*   **Test 91**: Should be 'A'. (Just above the line).

## 4. Practical Implementation: Range Checking
Use Python's chained comparison operators to succinctly define boundaries.

**Bad (Ambiguous)**:
```python
if x > 0 and x < 10:  # Is 0 included? Is 10 included?
    pass
```

**Good (Explicit)**:
```python
if 0 < x < 10:  # Exclusive
    pass

if 0 <= x <= 10:  # Inclusive
    pass
```

## 5. Summary
When you test, hunt for the edges. That is where the dragons live.

# Challenge: Advanced Algorithm Analysis

## 1. Lesson Focus
Testing intuition for Big-O notation, counting operations in loops, and comparing algorithm speeds.

## 2. Core Concepts
**Big-O Notation**: Describes how algorithm runtime grows as input size increases, focusing on the dominant term and dropping constants.

**Time Complexity Classes**:
- **O(1)**: Constant time—doesn't depend on input size
- **O(n)**: Linear time—grows proportionally with input size
- **O(n²)**: Quadratic time—grows with square of input size (nested loops)
- **O(2ⁿ)**: Exponential time—doubles with each additional input element

**Dominant Term**: When multiple terms exist (e.g., 3n² + 100n + 7), the fastest-growing term (n²) determines the overall Big-O.

## 3. Key Details to Remember
- Single loop over n items: O(n)
- Nested loops over n items: O(n²)
- Mixed code (nested + single): keep the fastest-growing term
- Linear scan worst case: O(n) (item at end or not present)
- Linear scan best case: O(1) (item at start)

## 4. How to Analyze Complexity
**Step 1**: Identify loops and their nesting depth
**Step 2**: Count operations per loop iteration
**Step 3**: Multiply for nested loops, add for sequential loops
**Step 4**: Keep only the dominant term, drop constants

## 5. Examples

### Example 1: Simple Loop
```python
total = 0
for i in range(n):
    total += i
```
**Complexity**: O(n)—loop runs n times.

### Example 2: Multiple Operations per Iteration
```python
ops = 0
for i in range(n):
    ops += 1  # runs n times
    ops += 2  # runs n times
```
**Complexity**: O(n)—both lines run n times total, not n².

### Example 3: Dominant Term
Algorithm does 3n² + 100n + 7 operations.
**Complexity**: O(n²)—n² dominates as n grows large.

### Example 4: Linear Scan (Worst Case)
```python
for item in list:
    if item == target:
        break
```
**Complexity**: O(n)—may check all n items.

### Example 5: Comparing Algorithms
```python
# Version A: Single loop
for i in range(n):
    print(i)

# Version B: Nested loops
for i in range(n):
    for j in range(n):
        print(i, j)
```
**Result**: Version A is faster—O(n) vs O(n²).

### Example 6: Mixed Code
```python
count = 0
for i in range(n):
    for j in range(n):
        count += 1  # n² operations
for k in range(n):
    count += 1  # n operations
```
**Complexity**: O(n²)—n² dominates over n.

## 6. Common Mistakes / What Not to Do
- **Counting operations incorrectly**: Multiple lines in a single loop still count as O(n), not O(n²).
- **Forgetting worst case**: Linear scan is O(n) in worst case, not O(2ⁿ).
- **Missing dominant term**: In mixed code, keep the fastest-growing term, don't add them.

## 7. Open-Note Review
- Single loop: O(n)
- Nested loops: O(n²)
- Linear scan worst case: O(n)
- Linear scan best case: O(1)
- Mixed code: keep dominant term
- 3n² + 100n + 7 → O(n²)

## 8. Final Takeaway
Big-O analysis focuses on growth rate—identify the dominant term and ignore constants to understand how algorithms scale.

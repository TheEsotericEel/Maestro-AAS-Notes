# Analyzing Algorithms with Big O

## 1. Introduction
Analyzing algorithms with Big O notation involves examining code patterns and mathematical expressions to determine how an algorithm's performance scales with input size. This lesson focuses on practical analysis techniques and dominant term identification.

## 2. Core Concepts Review

### 2.1 Big O Fundamentals
- **n**: Number of inputs/items the algorithm works on
- **Big O**: How the number of steps grows as n grows
- **Focus**: Growth rate, not exact performance

### 2.2 Growth Rate Impact
**Linear Algorithm (O(n))**:
- Double input → Double work
- Example: One sticker per kid

**Quadratic Algorithm (O(n²))**:
- Double input → 4× work
- Example: Compare every kid with every other kid

## 3. Mathematical Analysis

### 3.1 Dominant Term Principle
**Key Rule**: In Big O, we ignore constants and lower-order terms, focusing on the fastest-growing term.

**Example**: `3n + 5 steps`
- `3n` grows with n
- `+5` is constant
- **Big O**: O(n) (ignore +5 and the 3)

### 3.2 Step-by-Step Simplification

#### Example 1: Linear Expression
**Formula**: `10n + 100`
```
Step 1: Identify terms: 10n (grows), 100 (constant)
Step 2: Drop constant: 10n
Step 3: Ignore coefficient: n
Result: O(n)
```

#### Example 2: Quadratic Expression
**Formula**: `5n² + 3n + 2`
```
Step 1: Identify terms: 5n² (fastest), 3n (slower), 2 (constant)
Step 2: Drop lower terms: 5n²
Step 3: Ignore coefficient: n²
Result: O(n²)
```

#### Example 3: Complex Expression
**Formula**: `2n² + 50n + 1`
```
Step 1: n² term dominates as n gets large
Step 2: 50n grows slower than n²
Step 3: 1 is constant
Result: O(n²)
```

### 3.3 Why This Works
**As n grows large**:
- n² grows much faster than n
- Constants become insignificant
- The dominant term determines performance

## 4. Code Pattern Analysis

### 4.1 Single Loop Pattern
```python
for i in range(n):
    print(i)
```

**Analysis**:
- Loop runs n times
- Each iteration does constant work
- **Complexity**: O(n)

**Real-world Analogy**: Give one sticker to each kid in line

### 4.2 Nested Loop Pattern
```python
for i in range(n):
    for j in range(n):
        print(i, j)
```

**Analysis**:
- Outer loop: n iterations
- Inner loop: n iterations for each outer iteration
- Total operations: n × n = n²
- **Complexity**: O(n²)

**Real-world Analogy**: Compare every kid with every other kid

### 4.3 Mixed Pattern
```python
print("start")

for i in range(n):
    print(i)

print("end")
```

**Analysis**:
- `print("start")`: O(1)
- Loop: O(n)
- `print("end")`: O(1)
- Total: O(1) + O(n) + O(1) = O(n)

## 5. Advanced Pattern Combinations

### 5.1 Sequential Loops
```python
def sequential_loops(n):
    # First loop: O(n)
    for i in range(n):
        print(i)
    
    # Second loop: O(n)
    for j in range(n):
        print(j)
```

**Analysis**:
- First loop: O(n)
- Second loop: O(n)
- Total: O(n) + O(n) = O(2n) = O(n)

### 5.2 Nested and Sequential Mixed
```python
def mixed_patterns(n):
    # Loop A: O(n)
    for i in range(n):
        print(i)
    
    # Loop B with nesting: O(n²)
    for j in range(n):
        for k in range(n):
            print(j, k)
```

**Analysis**:
- Loop A: O(n)
- Loop B + inner: O(n²)
- Total: O(n) + O(n²) = O(n²)

### 5.3 Triple Nested Loop
```python
def triple_nested(n):
    for i in range(n):
        for j in range(n):
            for k in range(n):
                print(i, j, k)
```

**Analysis**:
- Three levels of nesting
- Total operations: n × n × n = n³
- **Complexity**: O(n³)

## 6. Analysis Methodology

### 6.1 Step-by-Step Process
1. **Identify Input Size**: What does n represent?
2. **Count Basic Operations**: What constitutes one step?
3. **Analyze Loops**: How many times do they run?
4. **Consider Nesting**: Multiply complexities for nested structures
5. **Combine Sequential Parts**: Add complexities, then simplify
6. **Apply Big O Rules**: Drop constants and lower-order terms

### 6.2 Quick Reference Guide

| Code Pattern | Complexity | Example |
|--------------|------------|---------|
| Single operation | O(1) | `x = 5` |
| Single loop | O(n) | `for i in range(n):` |
| Nested loops (2 levels) | O(n²) | `for i in range(n): for j in range(n):` |
| Nested loops (3 levels) | O(n³) | `for i in range(n): for j in range(n): for k in range(n):` |
| Sequential loops | O(n) | `for i in range(n):` followed by `for j in range(n):` |
| Logarithmic loop | O(log n) | `while i < n: i *= 2` |

## 7. Practical Examples

### 7.1 Linear Search
```python
def linear_search(items, target):
    for item in items:  # O(n)
        if item == target:  # O(1)
            return True
    return False
```

**Analysis**: O(n) × O(1) = O(n)

### 7.2 Finding Maximum
```python
def find_max(numbers):
    max_val = numbers[0]  # O(1)
    for num in numbers[1:]:  # O(n)
        if num > max_val:  # O(1)
            max_val = num
    return max_val
```

**Analysis**: O(1) + O(n) × O(1) = O(n)

### 7.3 Bubble Sort
```python
def bubble_sort(arr):
    n = len(arr)
    for i in range(n):  # O(n)
        for j in range(n - i - 1):  # O(n)
            if arr[j] > arr[j + 1]:  # O(1)
                arr[j], arr[j + 1] = arr[j + 1], arr[j]
```

**Analysis**: O(n) × O(n) × O(1) = O(n²)

### 7.4 Matrix Multiplication
```python
def matrix_multiply(A, B):
    n = len(A)
    result = [[0 for _ in range(n)] for _ in range(n)]
    for i in range(n):  # O(n)
        for j in range(n):  # O(n)
            for k in range(n):  # O(n)
                result[i][j] += A[i][k] * B[k][j]  # O(1)
    return result
```

**Analysis**: O(n) × O(n) × O(n) × O(1) = O(n³)

## 8. Common Mistakes and Corrections

### 8.1 Mistake 1: Counting Constants
**Wrong**: Saying `10n + 100` is O(10n)
**Correct**: It's O(n) - we ignore the 10

### 8.2 Mistake 2: Adding Complexities Incorrectly
**Wrong**: O(n) + O(n²) = O(2n²)
**Correct**: O(n) + O(n²) = O(n²) - n² dominates

### 8.3 Mistake 3: Missing Nested Structure
**Wrong**: Thinking nested loops are O(n)
**Correct**: Nested loops multiply complexities

### 8.4 Mistake 4: Overcomplicating Simple Cases
**Wrong**: Analyzing every line of code in detail
**Correct**: Focus on dominant patterns

## 9. Advanced Analysis Techniques

### 9.1 Recursive Algorithms
```python
def factorial(n):
    if n <= 1:
        return 1
    return n * factorial(n - 1)
```

**Analysis**: O(n) - one recursive call per n

### 9.2 Divide and Conquer
```python
def binary_search(arr, target, left, right):
    if left > right:
        return -1
    mid = (left + right) // 2
    if arr[mid] == target:
        return mid
    elif arr[mid] < target:
        return binary_search(arr, target, mid + 1, right)
    else:
        return binary_search(arr, target, left, mid - 1)
```

**Analysis**: O(log n) - halves the search space each time

### 9.3 Dynamic Programming
```python
def fibonacci_dp(n):
    if n <= 1:
        return n
    fib = [0, 1]
    for i in range(2, n + 1):
        fib.append(fib[i - 1] + fib[i - 2])
    return fib[n]
```

**Analysis**: O(n) - one loop from 2 to n

## 10. Practice Problems

### 10.1 Problem 1: Basic Analysis
What is the Big O complexity?
```python
def function_a(n):
    total = 0
    for i in range(n):
        total += i
    return total
```

**Answer**: O(n)

### 10.2 Problem 2: Nested Analysis
What is the Big O complexity?
```python
def function_b(n):
    for i in range(n):
        for j in range(n):
            print(i * j)
```

**Answer**: O(n²)

### 10.3 Problem 3: Mixed Analysis
What is the Big O complexity?
```python
def function_c(n):
    print("Starting")
    for i in range(n):
        print(i)
    for j in range(n):
        for k in range(n):
            print(j, k)
    print("Done")
```

**Answer**: O(n²)

### 10.4 Problem 4: Mathematical Expression
What is the Big O for: `7n² + 5n + 20`?

**Answer**: O(n²)

## 11. Real-World Applications

### 11.1 Database Operations
- **Index Lookup**: O(1) or O(log n)
- **Full Table Scan**: O(n)
- **Join Operations**: Often O(n²)

### 11.2 Web Applications
- **Rendering a List**: O(n)
- **Sorting User Data**: O(n log n)
- **Searching**: O(n) or O(log n) with index

### 11.3 Mobile Apps
- **Loading Contacts**: O(n)
- **Image Processing**: Often O(n²) or higher
- **GPS Navigation**: O(n²) for shortest path

## 12. Summary

### Key Takeaways
- **Dominant Term**: Focus on the fastest-growing part of the expression
- **Ignore Constants**: 10n + 100 becomes O(n), not O(10n)
- **Code Patterns**: Single loops = O(n), nested loops = O(n²)
- **Sequential Operations**: Add complexities, then take the dominant
- **Practice**: Recognition comes with analyzing many examples

### Core Insight
> **"Big O analysis is about identifying which part of your algorithm will dominate the running time as input size grows, then simplifying to focus only on that dominant behavior."**

### Analysis Checklist
- [ ] Identify n (input size)
- [ ] Find all loops and their nesting
- [ ] Count basic operations
- [ ] Calculate total complexity
- [ ] Apply Big O simplification rules
- [ ] Verify with examples

### Next Steps
- Practice with more complex algorithms
- Learn about space complexity
- Study specific algorithm families
- Explore optimization techniques

## 13. Quick Reference

### Common Big O Classes
| Notation | Name | Growth Rate | Example |
|----------|------|-------------|---------|
| O(1) | Constant | None | Array access |
| O(log n) | Logarithmic | Very slow | Binary search |
| O(n) | Linear | Proportional | Linear search |
| O(n log n) | Linearithmic | Faster than quadratic | Efficient sort |
| O(n²) | Quadratic | Accelerating | Bubble sort |
| O(n³) | Cubic | Very fast | Matrix multiplication |
| O(2ⁿ) | Exponential | Explosive | Subset generation |

### Analysis Rules
1. **Drop constants**: O(2n) = O(n)
2. **Drop lower terms**: O(n² + n) = O(n²)
3. **Nested loops multiply**: O(n) × O(m) = O(nm)
4. **Sequential loops add**: O(n) + O(m) = O(n + m)
5. **Take dominant**: O(n + n²) = O(n²)
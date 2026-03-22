# Challenge: Algorithm Analysis

## Learning Objectives
By the end of this challenge, you will be able to:
- Count primitive steps in Python functions
- Identify Big O complexity classes (O(1), O(n), O(n²), O(2ⁿ))
- Compare algorithm efficiency
- Analyze best-case and worst-case scenarios

## Introduction
Welcome to your algorithm analysis challenge! This lesson will test your understanding of how to count operations, analyze time complexity, and compare different algorithms. We'll work through multiple-choice questions that reinforce key concepts from previous lessons.

## Core Concepts Review

### Counting Primitive Steps
When analyzing algorithms, we count basic operations like:
- Assignments (`=`)
- Arithmetic operations (`+`, `-`, `*`, `/`)
- Comparisons (`<`, `>`, `==`)
- Array/list access (`nums[i]`)

### Big O Complexity Classes
- **O(1)** - Constant time: Same number of steps regardless of input size
- **O(n)** - Linear time: Steps grow proportionally with input size
- **O(n²)** - Quadratic time: Steps grow with the square of input size
- **O(2ⁿ)** - Exponential time: Steps double with each additional input element

## Practice Questions

### Question 1: Step Counting
**Problem:** How many primitive steps does this function perform?

```python
def add_first_three(nums):
    total = 0
    total += nums[0]
    total += nums[1]
    total += nums[2]
    return total
```

**Answer Analysis:**
- `total = 0` → 1 assignment
- `total += nums[0]` → 1 addition
- `total += nums[1]` → 1 addition
- `total += nums[2]` → 1 addition
- **Total: 4 steps** (constant, regardless of list length)

### Question 2: Best Case Analysis
**Problem:** In the best case, how many times is the condition `n < 0` checked?

```python
def has_negative(nums):
    for n in nums:
        if n < 0:
            return True
    return False
```

**Answer:** Exactly 1 time (if the first element is negative)

### Question 3: Linear Time Complexity
**Problem:** What is the Big O complexity of this function?

```python
def sum_list(nums):
    total = 0
    for n in nums:
        total += n
    return total
```

**Answer:** O(n) - Linear time
- The loop runs once for each element
- Doubling input size doubles the work

### Question 4: Comparing Nested Loops
**Problem:** Compare these two functions:

```python
# Version A
def find_first(nums, target):
    for n in nums:
        if n == target:
            return True
    return False

# Version B
def find_first(nums, target):
    for n in nums:
        for m in nums:
            if m == target:
                return True
    return False
```

**Answer:** Version A is O(n), Version B is O(n²)
- Version A: Single loop → linear
- Version B: Nested loops → quadratic

### Question 5: Constant vs Linear Time
**Problem:** Compare these functions:

```python
# Function A
def first_item(nums):
    return nums[0]

# Function B
def print_all(nums):
    for x in nums:
        print(x)
```

**Answer:** Function A is O(1), Function B is O(n)
- Function A: Single array access → constant
- Function B: Loop through all elements → linear

### Question 6: Quadratic Time
**Problem:** How many comparisons run in this function?

```python
def compare_pairs(nums):
    for i in range(len(nums)):
        for j in range(len(nums)):
            if nums[i] == nums[j]:
                pass
```

**Answer:** About n² comparisons
- Outer loop: n iterations
- Inner loop: n iterations per outer iteration
- Total: n × n = n²

### Question 7: Different Access Patterns
**Problem:** Compare these functions:

```python
# Function A
def check_first(nums):
    if nums[0] < 0:
        return True
    return False

# Function B
def check_all(nums):
    for x in nums:
        if x < 0:
            return True
    return False
```

**Answer:** Function A is O(1), Function B is O(n)
- Function A: Always checks first element only
- Function B: May check up to all elements

## Boss Question: Exponential Time

**Problem:** What is the Big O complexity of generating all subsets of a list?

```python
def all_subsets(nums):
    subsets = []
    # generates every possible subset of nums
    return subsets
```

**Answer:** O(2ⁿ) - Exponential time
- A list of length n has 2ⁿ possible subsets
- Each subset requires work to generate
- Growth rate: 2ⁿ is much faster than n²

## Key Takeaways

### Recognizing Complexity Patterns
- **O(1)**: Single operations, array access by index
- **O(n)**: Single loops, linear scans
- **O(n²)**: Nested loops over same data
- **O(2ⁿ)**: Generating all combinations/subsets

### Best vs Worst Case
- **Best case**: Minimum work needed (often O(1) for search operations)
- **Worst case**: Maximum work needed (depends on algorithm structure)

### Algorithm Comparison
- Lower Big O is generally better
- Consider both time and space complexity
- Real-world factors matter (constants, hardware)

## Challenge Exercise

**Problem:** Analyze the complexity of this function and explain your reasoning:

```python
def mystery_function(nums):
    count = 0
    for i in range(len(nums)):
        for j in range(i, len(nums)):
            if nums[i] + nums[j] == 10:
                count += 1
    return count
```

**Hint:** The inner loop doesn't always run n times...

## Review

You've mastered:
- ✅ Counting primitive operations
- ✅ Identifying Big O complexity classes
- ✅ Comparing algorithm efficiency
- ✅ Understanding best vs worst case scenarios
- ✅ Recognizing exponential growth patterns

These skills are fundamental for designing efficient algorithms and understanding performance trade-offs in software development.

## Next Steps
Ready to move on to more advanced algorithmic concepts? Your understanding of complexity analysis will be crucial for:
- Sorting algorithms
- Data structure selection
- Optimization techniques
- System design decisions

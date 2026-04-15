# Challenge: Sorting

## 1. Lesson Focus
Testing understanding of bubble sort, insertion sort, time complexity, and Python's built-in sorting functions through practical challenges.

## 2. Core Concepts
**Bubble Sort**: Repeatedly walks the list swapping adjacent elements that are out of order, until a full pass makes no swaps.

**Insertion Sort**: Grows a sorted prefix on the left by taking each new element and shifting larger elements right to insert it into its correct position.

**Time Complexity Classes**:
- Constant (O(1)): doesn't depend on input size
- Linear (O(n)): grows proportionally with input size
- Quadratic (O(n²)): grows with square of input size

**Python sorted()**: Built-in function with `key` parameter for custom sorting criteria and `reverse` for order direction.

## 3. Key Details to Remember
- Bubble sort: neighbor swaps, O(n²)
- Insertion sort: shifts and inserts, O(n²) average, O(n) best case
- Insertion sort preferred for nearly sorted data
- Bubble sort acceptable for small random lists
- `sorted(iterable, key=function, reverse=True)` pattern

## 4. Implementation Patterns

**Insertion Sort Inner Loop**:
```python
while j >= 0 and arr[j] > key:
    arr[j + 1] = arr[j]  # shift element right
    j -= 1               # move left
arr[j + 1] = key  # insert key in correct spot
```

**Python sorted() with Custom Key**:
```python
sorted(words, key=len, reverse=True)
```

## 5. Examples

### Example 1: Bubble Sort Trace
**Input**: [5, 1, 4, 2, 3]
**After first pass**: [1, 4, 2, 3, 5]
- Compare 5 and 1 → swap → [1, 5, 4, 2, 3]
- Compare 5 and 4 → swap → [1, 4, 5, 2, 3]
- Compare 5 and 2 → swap → [1, 4, 2, 5, 3]
- Compare 5 and 3 → swap → [1, 4, 2, 3, 5]

### Example 2: Sorting by Length
```python
words = ["algorithm", "data", "sort", "bubble", "insertion"]
result = sorted(words, key=len, reverse=True)
# Output: ['algorithm', 'insertion', 'bubble', 'sort', 'data']
```

## 6. Algorithm Selection Guidelines

**Choose Insertion Sort When**:
- Nearly sorted data (few elements out of place)
- Want fewer element movements
- Data frequently arrives in nearly-sorted order

**Choose Bubble Sort When**:
- Small random lists
- Simplicity is priority
- Educational purposes

## 7. Time Complexity Identification
- Return first element: constant time O(1)
- Single loop through list: linear time O(n)
- Nested loops: quadratic time O(n²)

## 8. Common Mistakes / What Not to Do
- **Forgetting key parameter**: When sorting by property (like length), always use `key=`.
- **Confusing sort order**: Use `reverse=True` for descending order.
- **Wrong algorithm choice**: Don't use bubble sort on nearly sorted large data—insertion sort is better.

## 9. Open-Note Review
- Bubble sort: neighbor swaps, O(n²)
- Insertion sort: shifts and inserts, O(n²) average, O(n) best
- Nearly sorted → insertion sort
- Small random → either is fine
- Time complexity: constant, linear, quadratic
- Python: `sorted(iterable, key=func, reverse=True)`

## 10. Final Takeaway
Choose sorting algorithms based on data characteristics—insertion sort for nearly sorted data, bubble sort for simple cases—and use Python's `sorted()` with `key` for custom sorting criteria.

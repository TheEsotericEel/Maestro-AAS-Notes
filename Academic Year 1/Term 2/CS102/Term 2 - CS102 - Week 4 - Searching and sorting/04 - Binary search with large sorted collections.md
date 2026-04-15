# Binary Search with Large Sorted Collections

## 1. Lesson Focus
Understanding binary search algorithm, how it works by repeatedly halving the search range, and why it requires sorted data.

## 2. Core Concepts
**Binary Search**: Search algorithm that starts in the middle of a sorted collection and repeatedly halves the search range until the target is found or the range is empty.

**Low, High, Mid Indices**: Three pointers used to track the current search range:
- `low`: start of current search range
- `high`: end of current search range
- `mid`: middle index between low and high

**Sorted Data Requirement**: Binary search only works if everything left of mid is smaller and everything right of mid is larger—this property only holds for sorted data.

## 3. Key Details to Remember
- Binary search cuts the search range in half each iteration
- Time complexity: O(log n) — much faster than linear search O(n)
- For 1,000 items: ~10 checks vs 1,000 checks for linear search
- Must have sorted data to work correctly
- Uses while loop with condition `low <= high`

## 4. Algorithm / Process
**Binary Search Steps**:
1. Set `low = 0`, `high = len(arr) - 1`
2. While `low <= high`:
   - Calculate `mid = (low + high) // 2`
   - If `arr[mid] == target`: return `mid`
   - If `arr[mid] < target`: target is in right half, set `low = mid + 1`
   - If `arr[mid] > target`: target is in left half, set `high = mid - 1`
3. If loop exits, return -1 (not found)

## 5. Examples

### Example 1: Basic Binary Search Implementation
```python
def binary_search(arr, target):
    low = 0
    high = len(arr) - 1

    while low <= high:
        mid = (low + high) // 2

        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            low = mid + 1
        else:
            high = mid - 1

    return -1

numbers = [3, 7, 12, 18, 25, 31, 40]
target = 18
index = binary_search(numbers, target)
print("Result index:", index)  # Output: 3
```

### Example 2: Multi-Step Trace
```python
numbers = [3, 7, 12, 18, 25, 31, 40, 55, 72]
target = 31

# Iteration 1:
# low=0, high=8, mid=4, arr[4]=25
# 25 < 31 → search right half
# low=5, high=8

# Iteration 2:
# low=5, high=8, mid=6, arr[6]=40
# 40 > 31 → search left half
# low=5, high=5

# Iteration 3:
# low=5, high=5, mid=5, arr[5]=31
# Found! Return 5
```

## 6. Why Sorted Data is Required
Binary search relies on the assumption:
- Everything left of mid is smaller
- Everything right of mid is larger

**Unsorted Example**: `[18, 3, 31, 7, 40, 12, 25]`
- Mid might be 7
- Searching for 31 (> 7) doesn't guarantee it's on the right
- Target could be anywhere—halving fails

**Sorted Example**: `[3, 7, 12, 18, 25, 31, 40]`
- Mid is 18
- Searching for 31 (> 18) guarantees it's on the right
- Halving works correctly

## 7. Performance Comparison
**Linear Search (O(n))**: 1,000 items → up to 1,000 checks
**Binary Search (O(log n))**: 1,000 items → ~10 checks

Halving progression: 1,000 → 500 → 250 → 125 → 62 → 31 → 16 → 8 → 4 → 2 → 1

## 8. Common Mistakes / What Not to Do
- **Using binary search on unsorted data**: Algorithm will fail—data must be sorted.
- **Incorrect mid calculation**: Use `(low + high) // 2` for integer division.
- **Wrong loop condition**: Use `low <= high`, not `low < high`.
- **Forgetting to update low/high**: Must adjust range based on comparison with target.

## 9. Open-Note Review
- Binary search = start middle, halve range, repeat
- Time complexity: O(log n)
- Requires sorted data
- Track low, high, mid indices
- Much faster than linear search for large datasets

## 10. Final Takeaway
Binary search dramatically speeds up searching large sorted collections by repeatedly halving the search range, but only works when data is sorted.

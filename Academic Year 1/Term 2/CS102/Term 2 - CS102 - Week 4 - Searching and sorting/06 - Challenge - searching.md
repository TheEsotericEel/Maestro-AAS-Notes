# Challenge: Searching

## 1. Lesson Focus
Testing understanding of search concepts, linear vs binary search selection, implementation details, and performance characteristics.

## 2. Core Concepts
**Search Identification**: Recognizing when a process involves searching vs direct access.

**Search Selection**: Choosing between linear and binary search based on data size, sorted status, and frequency of use.

**Linear Search Implementation**: Simple loop comparing each element to target.

**Binary Search Tracing**: Tracking low, high, mid indices through halving process.

## 3. Key Details to Remember
- Linear search: check items one by one, O(n) complexity
- Binary search: halving approach, O(log n) complexity
- Binary requires sorted data
- Linear fine for small lists, binary better for large sorted lists
- Worst case linear: check all n items

## 4. Implementation Patterns

**Linear Search Pattern**:
```python
def linear_search(nums, target):
    for i in range(len(nums)):
        if nums[i] == target:
            return i
    return -1
```

**Binary Search Index Updates**:
- If `arr[mid] < target`: `low = mid + 1` (search right half)
- If `arr[mid] > target`: `high = mid - 1` (search left half)
- If `arr[mid] == target`: return `mid`

## 5. Binary Search Tracing Example
```python
# List: [3, 8, 12, 20, 25, 31, 40]
# Index:  0  1   2   3   4   5   6
# Target: 25

# Step 1:
low = 0, high = 6
mid = (0 + 6) // 2 = 3
arr[3] = 20
20 < 25 → move right
low = 4, high = 6

# Step 2:
mid = (4 + 6) // 2 = 5
arr[5] = 31
31 > 25 → move left
low = 4, high = 4

# Step 3:
mid = (4 + 4) // 2 = 4
arr[4] = 25
Found! Return 4
```

## 6. Search Selection Criteria

**Choose Linear Search When**:
- Small datasets (like 7 items)
- Unsorted data
- One-time search
- Simple implementation sufficient

**Choose Binary Search When**:
- Large datasets (thousands+ items)
- Sorted data
- Frequent lookups
- Performance matters

## 7. Performance Comparison
- Linear search on 9 items: worst case 9 checks
- Binary search on large sorted lists: far fewer checks than linear
- Binary search advantage increases with data size

## 8. Common Mistakes / What Not to Do
- **Confusing values with indices**: Binary search tracks index positions (low, high, mid), not the actual values.
- **Forgetting sorted requirement**: Binary search only works on sorted data.
- **Over-engineering small searches**: Linear is fine for tiny lists even if sorted.
- **Incorrect index updates**: Remember `low = mid + 1` and `high = mid - 1`, not just `mid`.

## 9. Open-Note Review
- Linear search: simple loop, O(n)
- Binary search: halving, O(log n), requires sorted data
- Small/unsorted/once → linear
- Large/sorted/frequent → binary
- Trace indices (low, high, mid), not values
- Worst case linear = n checks

## 10. Final Takeaway
Select search method based on data characteristics—linear for simple cases, binary for large sorted data with repeated lookups.

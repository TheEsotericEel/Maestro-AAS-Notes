# Bubble Sort

## 1. Lesson Focus
Understanding bubble sort algorithm—how it works by repeatedly swapping adjacent elements until the list is sorted.

## 2. Core Concepts
**Bubble Sort**: Sorting algorithm that repeatedly scans the list and swaps neighboring elements that are in the wrong order.

**Pass**: One complete walk through the list from start to end, comparing and swapping adjacent elements.

**Stopping Condition**: Algorithm stops when a full pass makes zero swaps, indicating the list is sorted.

**Bubbling Effect**: Largest elements gradually "bubble up" to the end of the list with each pass.

## 3. Key Details to Remember
- Compare adjacent elements (neighbors) only
- Swap if they're in wrong order
- Repeat passes until no swaps occur
- Time complexity: O(n²) in worst/average case
- Simple to understand and implement
- Not efficient for large datasets

## 4. Algorithm / Process
**Bubble Sort Steps**:
1. Start at the beginning of the list
2. Compare the first two adjacent elements
3. If they're in wrong order, swap them
4. Move to the next pair and compare
5. Continue to end of list (one pass)
6. Repeat passes until a complete pass makes no swaps

## 5. Examples

### Example 1: Manual Trace
**Start**: [4, 1, 3, 2]

**Pass 1**:
- Compare 4 and 1 → wrong order → swap → [1, 4, 3, 2]
- Compare 4 and 3 → wrong order → swap → [1, 3, 4, 2]
- Compare 4 and 2 → wrong order → swap → [1, 3, 2, 4]

**Result after pass 1**: [1, 3, 2, 4] (largest element 4 bubbled to end)

### Example 2: Another Trace
**Start**: [3, 2, 1]

**Pass 1**:
- Compare 3 and 2 → swap → [2, 3, 1]
- Compare 3 and 1 → swap → [2, 1, 3]

**Result after pass 1**: [2, 1, 3]

### Example 3: Python Implementation
```python
nums = [5, 1, 4, 2]
n = len(nums)

for i in range(n):  # each loop is one pass
    for j in range(0, n - 1):  # walk through neighbors
        if nums[j] > nums[j + 1]:
            # swap neighbors
            nums[j], nums[j + 1] = nums[j + 1], nums[j]
            print("swap made:", nums)

print("final:", nums)
```

**Output**:
```
swap made: [1, 5, 4, 2]
swap made: [1, 4, 5, 2]
swap made: [1, 4, 2, 5]
swap made: [1, 4, 2, 5]
swap made: [1, 2, 4, 5]
swap made: [1, 2, 4, 5]
final: [1, 2, 4, 5]
```

## 6. Common Mistakes / What Not to Do
- **Forgetting the stopping condition**: Must track whether any swaps occurred in a pass—stop when pass has zero swaps.
- **Comparing non-adjacent elements**: Bubble sort only compares immediate neighbors, not arbitrary pairs.
- **Inefficient implementation**: Without optimization, bubble sort always does n passes even if sorted early.

## 7. Open-Note Review
- Bubble sort = swap adjacent out-of-order neighbors
- Repeat passes until no swaps in a full pass
- Largest elements bubble to the end each pass
- Time complexity: O(n²)
- Simple but inefficient for large data

## 8. Final Takeaway
Bubble sort repeatedly walks through the list swapping adjacent elements that are out of order, stopping when a complete pass makes no swaps.

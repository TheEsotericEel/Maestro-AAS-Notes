# Insertion Sort

## 1. Lesson Focus
Understanding insertion sort algorithm—how it builds a sorted prefix by inserting each element into its correct position.

## 2. Core Concepts
**Insertion Sort**: Sorting algorithm that maintains a growing sorted prefix on the left and inserts each new element into its correct position by shifting larger elements right.

**Sorted Prefix**: The left portion of the list that is already sorted; grows from index 0 to the right.

**Key**: The current element being inserted into the sorted prefix.

**Shifting**: Moving elements one position to the right to make room for the key.

## 3. Key Details to Remember
- Start with element at index 0 as initial sorted prefix
- For each subsequent element, insert it into the correct position in the sorted prefix
- Shift larger elements right to make space
- Time complexity: O(n²) average/worst case, O(n) best case (already sorted)
- Efficient for small or nearly-sorted datasets
- "Placing" approach vs "bubbling" approach of bubble sort

## 4. Algorithm / Process
**Insertion Sort Steps**:
1. Treat index 0 as sorted prefix of length 1
2. For each index i from 1 to n-1:
   - Store arr[i] as key
   - Compare key with elements to its left (j = i-1, i-2, ...)
   - While arr[j] > key, shift arr[j] right and move j left
   - Insert key at position j+1
3. Repeat until all elements are in sorted prefix

## 5. Examples

### Example 1: Manual Trace
**Start**: [4, 2, 5, 1, 3]

**Step 1**: Insert 2
- Sorted prefix: [4]
- 2 < 4, shift 4 right
- Insert 2 at position 0
- Result: [2, 4, 5, 1, 3]

**Step 2**: Insert 5
- Sorted prefix: [2, 4]
- 5 > 4, already in place
- Result: [2, 4, 5, 1, 3]

**Step 3**: Insert 1
- Sorted prefix: [2, 4, 5]
- 1 < 5, shift 5 right
- 1 < 4, shift 4 right
- 1 < 2, shift 2 right
- Insert 1 at position 0
- Result: [1, 2, 4, 5, 3]

**Step 4**: Insert 3
- Sorted prefix: [1, 2, 4, 5]
- 3 < 5, shift 5 right
- 3 < 4, shift 4 right
- 3 > 2, insert at position 2
- Result: [1, 2, 3, 4, 5]

### Example 2: Python Implementation
```python
def insertion_sort(arr):
    for i in range(1, len(arr)):
        key = arr[i]      # element to insert
        j = i - 1         # start comparing with element before

        while j >= 0 and arr[j] > key:
            arr[j + 1] = arr[j]  # shift element right
            j -= 1               # move left

        arr[j + 1] = key  # insert key in correct spot

    return arr

print(insertion_sort([4, 2, 5, 1, 3]))  # [1, 2, 3, 4, 5]
```

## 6. Performance Characteristics

**Best Case (Already Sorted)**: O(n)
- Each element already in correct position
- Inner while loop rarely runs
- One comparison per element

**Average Case**: O(n²)
- Each element shifts through about half of sorted prefix
- n/2 comparisons per element × n elements

**Worst Case (Reverse Sorted)**: O(n²)
- Each element must shift through entire sorted prefix
- Maximum comparisons and shifts

**Test Cases**:
```python
print(insertion_sort([1, 2, 3, 4, 5]))       # Already sorted: O(n)
print(insertion_sort([1, 2, 3, 5, 4]))       # Nearly sorted: close to O(n)
print(insertion_sort([5, 4, 3, 2, 1]))       # Reverse sorted: O(n²)
```

## 7. Common Mistakes / What Not to Do
- **Forgetting to shift elements**: Must move larger elements right, not just swap.
- **Incorrect while condition**: Need `j >= 0 and arr[j] > key` to avoid index errors.
- **Off-by-one errors**: Insert at `j + 1`, not `j`, after loop exits.
- **Confusing with bubble sort**: Insertion sort places elements, doesn't repeatedly swap neighbors.

## 8. Open-Note Review
- Insertion sort = grow sorted prefix, insert each element into correct position
- Shift larger elements right to make space
- Time complexity: O(n²) average, O(n) best case (already sorted)
- Efficient for small or nearly-sorted data
- "Placing" approach vs bubble sort's "bubbling"

## 9. Final Takeaway
Insertion sort builds a sorted prefix by repeatedly inserting each new element into its correct position, shifting larger elements right—efficient for nearly-sorted data.

# Comparing Linear and Binary Search

## 1. Lesson Focus
Comparing linear and binary search performance, understanding how their step counts grow with data size, and choosing the right search for different scenarios.

## 2. Core Concepts
**Linear Search Growth**: Steps grow linearly with list size—if you multiply items by 10, steps also multiply by 10.

**Binary Search Growth**: Steps grow much slower than linear because it keeps cutting the list in half—logarithmic growth.

**Growth Comparison**: Linear is O(n), binary is O(log n)—dramatically different scaling behavior.

## 3. Step Count Comparison

**Linear Search (O(n))**:
- 10 items → ~10 checks
- 100 items → ~100 checks
- 1,000 items → ~1,000 checks
- 50,000 items → ~50,000 checks

**Binary Search (O(log n))**:
- 10 items → ~4 checks
- 100 items → ~7 checks
- 1,000 items → ~10 checks
- 50,000 items → ~16 checks

## 4. When to Use Each Search

**Use Linear Search When**:
- Small datasets (5-10 items)
- Unsorted data
- One-time search
- Simple implementation needed

**Use Binary Search When**:
- Large datasets (thousands+ items)
- Sorted data
- Many repeated lookups
- Performance matters

## 5. Scenario Examples

**Scenario 1: Small, Unsorted, One-Time**
- List: 7 unsorted numbers
- Search once
- Choice: Linear search
- Reason: Too small to benefit from binary, sorting would be overkill

**Scenario 2: Large, Sorted, Frequent**
- List: 50,000 sorted usernames on server
- Many checks per second
- Choice: Binary search
- Reason: Much faster on large sorted data with repeated lookups

## 6. Growth Language
- Linear search: steps grow linearly with list size
- Binary search: steps grow much slower than linear (logarithmic)

## 7. Common Mistakes / What Not to Do
- **Using binary search on unsorted data**: Algorithm will fail—requires sorted data.
- **Over-engineering with binary search**: For tiny datasets, linear is simpler and sufficient.
- **Ignoring frequency**: If searching once, linear may be fine even on larger data.

## 8. Open-Note Review
- Linear: O(n), steps grow linearly with size
- Binary: O(log n), steps grow much slower
- Small/unsorted/once → linear is fine
- Large/sorted/frequent → binary is much faster
- 1,000 items: linear ~1,000 checks, binary ~10 checks

## 9. Final Takeaway
Choose search based on data size, sorted status, and search frequency—linear for simple cases, binary for large sorted data with repeated lookups.

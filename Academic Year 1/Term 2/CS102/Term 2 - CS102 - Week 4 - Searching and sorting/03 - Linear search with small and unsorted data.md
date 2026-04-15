# Linear Search with Small and Unsorted Data

## 1. Lesson Focus
Understanding linear search, how to implement it in Python, and when it's the appropriate choice for small, unsorted datasets.

## 2. Core Concepts
**Linear Search**: Checking items one by one in a collection until you either find the target or run out of items.

**Early Termination**: Stopping the search immediately when the target is found (using `break`), rather than continuing through the entire collection.

**Return Convention**: Returning the index when target is found, or -1 when target is not found.

## 3. Key Details to Remember
- Linear search works on unsorted data
- Best for small datasets (5-10 items)
- Simple to implement and understand
- Time complexity: O(n)
- Stops early when target is found

## 4. Implementation Pattern
```python
def linear_search(target, collection):
    for i in range(len(collection)):
        if collection[i] == target:
            return i  # found, return index
    return -1  # not found
```

## 5. Examples

### Example 1: Basic Linear Search
```python
numbers = [5, 9, 2, 7, 4]
target = 7

found = False

for num in numbers:
    if num == target:
        found = True
        break  # stop as soon as we find it

if found:
    print("Found!")
else:
    print("Not found.")
```

### Example 2: Function with Index Return
```python
def find_pet(name, shelter_list):
    for i in range(len(shelter_list)):
        if shelter_list[i] == name:
            return i  # return index where found
    return -1  # not found

pets = ["Milo", "Luna", "Charlie", "Bella", "Max"]

print(find_pet("Charlie", pets))  # Output: 2
print(find_pet("Rocky", pets))   # Output: -1
```

## 6. When to Use Linear Search
**Ideal for:**
- Small datasets (5-10 items)
- Unsorted data (no structure to leverage)
- Data that changes frequently
- Simple, quick implementation needed

**Not ideal for:**
- Large datasets (1,000,000+ items)
- Static data that could be sorted/indexed
- Performance-critical applications

## 7. Common Mistakes / What Not to Do
- **Forgetting early termination**: Always use `break` or `return` when target is found to avoid unnecessary iterations.
- **Using wrong return value**: Return -1 for "not found" is a common convention, not 0 or False.
- **Overusing on large datasets**: Linear search becomes slow with large, unsorted data.

## 8. Open-Note Review
- Linear search = check items one by one
- Stop early when target found
- Return index if found, -1 if not
- Best for small, unsorted data
- Time complexity: O(n)

## 9. Final Takeaway
Linear search is simple and effective for small, unsorted datasets—check each item in order and stop when the target is found.

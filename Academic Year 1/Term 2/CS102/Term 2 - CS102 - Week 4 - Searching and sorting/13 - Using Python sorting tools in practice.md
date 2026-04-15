# Using Python Sorting Tools in Practice

## 1. Lesson Focus
Understanding Python's built-in sorting functions—`sorted()` vs `.sort()`, ascending/descending order, and custom sorting with the `key` parameter.

## 2. Core Concepts
**sorted()**: Built-in function that returns a new sorted list, leaving the original unchanged.

**list.sort()**: Method that sorts the list in place, modifying the original list without returning a new one.

**reverse=True**: Parameter that sorts in descending order (largest to smallest instead of smallest to largest).

**key Parameter**: Function that extracts a comparison key from each element for custom sorting (e.g., sorting by a specific field in a tuple).

**Lambda Function**: Anonymous function used with `key` to specify custom sorting logic (e.g., `lambda p: p[1]` to sort by second element).

## 3. Key Details to Remember
- `sorted()` returns new list, original unchanged
- `.sort()` modifies list in place
- `reverse=True` for descending order
- `key=lambda x: x[field]` for custom sorting
- Much easier/faster than implementing bubble sort or insertion sort manually

## 4. Syntax Patterns

**Basic Sorting**:
```python
sorted_scores = sorted(scores)  # new list, original unchanged
scores.sort()  # modifies original in place
```

**Descending Order**:
```python
sorted_scores = sorted(scores, reverse=True)  # largest to smallest
```

**Custom Key Sorting**:
```python
sorted_players = sorted(players, key=lambda p: p[1], reverse=True)
```

## 5. Examples

### Example 1: sorted() vs .sort()
```python
scores = [12, 5, 30, 18]

# sorted() - returns new list
sorted_scores = sorted(scores)
# scores = [12, 5, 30, 18] (unchanged)
# sorted_scores = [5, 12, 18, 30]

# .sort() - modifies in place
scores.sort()
# scores = [5, 12, 18, 30] (modified)
```

### Example 2: Descending Order
```python
scores = [12, 5, 30, 18]
sorted_scores = sorted(scores, reverse=True)
# Output: [30, 18, 12, 5]
```

### Example 3: Custom Sorting by Score
```python
players = [
    ("Alice", 15),
    ("Bob", 30),
    ("Cara", 22),
]

# Sort by score, highest first
sorted_players = sorted(players, key=lambda p: p[1], reverse=True)
# Output: [('Bob', 30), ('Cara', 22), ('Alice', 15)]

# Sort by score, lowest first
sorted_players = sorted(players, key=lambda p: p[1])
# Output: [('Alice', 15), ('Cara', 22), ('Bob', 30)]
```

## 6. Common Mistakes / What Not to Do
- **Confusing sorted() and .sort()**: `sorted()` returns new list, `.sort()` modifies in place.
- **Forgetting key parameter**: When sorting complex data, must use `key=` to specify what to sort by.
- **Wrong reverse usage**: `reverse=True` gives descending order, not ascending.
- **Default sorting on tuples**: Without `key`, tuples sort by first element only.

## 7. Open-Note Review
- `sorted()` returns new list, original unchanged
- `.sort()` modifies list in place
- `reverse=True` for descending order
- `key=lambda x: x[field]` for custom sorting
- Much easier than manual sorting algorithms

## 8. Final Takeaway
Use Python's built-in `sorted()` with `key` and `reverse` parameters for efficient, readable custom sorting instead of implementing algorithms manually.

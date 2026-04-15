# Advanced Sorting with Python Sorting Tools

## 1. Lesson Focus
Advanced sorting techniques using Python's `sorted()` function—multi-criteria sorting with tuple keys, sign flips for descending order, and choosing between data structures.

## 2. Core Concepts
**Tuple Key**: Using a tuple as the sorting key to implement multi-criteria sorting—Python compares tuple elements in order.

**Sign Flip**: Negating a value (`-value`) to reverse sort order without using `reverse=True`, useful when combining ascending and descending criteria.

**Multi-Criteria Sorting**: Sorting by primary field, then using secondary fields as tiebreakers when primary values are equal.

**List of Dicts vs Tuples**: Dicts provide clearer field access (`item["field"]`) compared to tuple indexing (`item[0]`).

## 3. Key Details to Remember
- Tuple keys compare elements in order: first element primary, subsequent elements tiebreakers
- `-value` flips ascending to descending for numeric fields
- `sorted()` returns new list, `.sort()` modifies in place
- Prefer built-in `sorted()` over manual sorting algorithms in production code
- Dicts are often clearer than tuples for complex data structures

## 4. Multi-Criteria Sorting Patterns

**Primary Descending, Secondary Ascending**:
```python
key=lambda p: (-p["score"], p["name"])
# Higher scores first, then A→Z names for ties
```

**Primary Ascending, Secondary Descending**:
```python
key=lambda p: (p["age"], -p["height"])
# Younger first, then taller for same age
```

**Primary and Secondary Both Ascending**:
```python
key=lambda t: (t["priority"], t["time"])
# Priority ascending, time ascending as tiebreaker
```

## 5. Examples

### Example 1: Leaderboard with Tiebreaker
```python
players = [
    ("Alex", 50),
    ("Jordan", 80),
    ("Blake", 80),
    ("Casey", 40),
]

# Sort by score descending, then name A→Z
sorted_players = sorted(players, key=lambda p: (-p[1], p[0]))
# Output: [('Blake', 80), ('Jordan', 80), ('Alex', 50), ('Casey', 40)]
```

### Example 2: Task List with Priority and Time
```python
tasks = [
    {"title": "Wash dishes", "priority": 2, "time": 10},
    {"title": "Finish project", "priority": 1, "time": 60},
    {"title": "Reply to emails", "priority": 3, "time": 20},
    {"title": "Workout", "priority": 1, "time": 30},
]

# Sort by priority ascending, then time ascending
sorted_tasks = sorted(tasks, key=lambda t: (t["priority"], t["time"]))
```

### Example 3: Products by Rating and Price
```python
products = [
    {"name": "Widget", "price": 10, "rating": 4.5},
    {"name": "Gadget", "price": 25, "rating": 4.8},
    {"name": "Doohickey", "price": 15, "rating": 4.8},
    {"name": "Thingamajig", "price": 5, "rating": 4.2},
]

# Sort by rating descending, then price ascending
sorted_products = sorted(products, key=lambda p: (-p["rating"], p["price"]))
# Output: Doohickey (4.8, $15), Gadget (4.8, $25), Widget (4.5, $10), Thingamajig (4.2, $5)
```

### Example 4: Students by Grade and Name
```python
students = [
    {"name": "Alex", "grade": 90},
    {"name": "Jordan", "grade": 85},
    {"name": "Blake", "grade": 90},
    {"name": "Casey", "grade": 70},
]

# Sort by grade descending, then name A→Z
sorted_students = sorted(students, key=lambda s: (-s["grade"], s["name"]))
```

## 6. Data Structure Choice

**Tuples**:
```python
("Alex", 87)
# Access: p[0], p[1]
# Less self-documenting
```

**Dicts**:
```python
{"name": "Alex", "grade": 87}
# Access: p["name"], p["grade"]
# More self-documenting, clearer
```

## 7. When to Use Built-in vs Manual Sorting

**Use Built-in sorted() When**:
- Production code
- Need clear, concise implementation
- Want fast, optimized sorting
- Standard sorting requirements

**Write Manual Sort When**:
- Learning exercise
- Very unusual constraints built-ins can't express
- Custom algorithm requirements

**Benefits of Built-in**:
- Fast enough for almost all use cases
- Short, clear code
- Less room for bugs

## 8. Common Mistakes / What Not to Do
- **Confusing reverse=True with sign flips**: `reverse=True` reverses entire sort; use sign flips in tuple keys for mixed ascending/descending criteria.
- **Wrong tuple order**: First element in tuple is primary sort field, not last.
- **Forgetting sorted() returns new list**: `.sort()` modifies in place and returns None.
- **Using index 0/1 on dicts**: Dicts use string keys, not integer indices.

## 9. Open-Note Review
- Tuple keys for multi-criteria: (primary, secondary, ...)
- Sign flip `-value` for descending without reverse=True
- Dicts clearer than tuples: `item["field"]` vs `item[0]`
- Use `sorted()` in production, not manual algorithms
- Multi-criteria: compare tuple elements in order

## 10. Final Takeaway
Use tuple keys with sign flips for multi-criteria sorting in Python—prefer built-in `sorted()` over manual sorting algorithms for production code.

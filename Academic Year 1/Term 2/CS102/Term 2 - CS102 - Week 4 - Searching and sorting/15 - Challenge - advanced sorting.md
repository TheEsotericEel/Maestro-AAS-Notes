# Challenge: Advanced Sorting

## 1. Lesson Focus
Testing understanding of Python's sorting functions through multiple-choice questions covering `sorted()` vs `.sort()`, ascending/descending order, custom keys, and practical decision-making.

## 2. Core Concepts
**sorted() vs .sort()**: `sorted()` returns a new list leaving original unchanged, `.sort()` modifies list in place.

**reverse=True**: Parameter for descending order (largest to smallest).

**key Parameter**: Function for custom sorting criteria (e.g., `key=len` for length, `key=lambda p: p[1]` for tuple field).

**Tuple Keys**: Multi-criteria sorting using tuples like `(-p["rating"], p["price"])` for combined ascending/descending criteria.

**Sign Flip**: Negating values (`-value`) to reverse order without `reverse=True`, useful in tuple keys.

## 3. Key Details to Remember
- `sorted()` returns new list, `.sort()` modifies in place
- `reverse=True` for descending order
- `key=len` sorts by string length
- `key=lambda p: p[1]` sorts by second element of tuple
- `key=lambda p: (-p["rating"], p["price"])` for rating descending, price ascending
- Use built-in `sorted()` in production, not manual algorithms

## 4. Quiz Review

**Question 1**: sorted() vs .sort() behavior
- `scores.sort()` modifies original to [10, 20, 30]
- `sorted(scores)` returns new sorted copy
- Both end up as [10, 20, 30] after sequence

**Question 2**: Descending order
- `sorted(heights, reverse=True)` or `heights.sort(reverse=True)`
- Use `reverse=True` for tallest to shortest

**Question 3**: Sort by length
- `sorted(pets, key=len)` sorts by name length ascending
- `key=len` is the function, not `len()`

**Question 4**: Tuple sorting by score
- `sorted(players, key=lambda p: p[1], reverse=True)` for highest to lowest
- `p[1]` is the score field

**Question 5**: Multi-criteria with dicts
- `key=lambda p: (-p["rating"], p["price"])`
- `-p["rating"]` for rating descending, `p["price"]` for price ascending

**Question 6**: Practical decision
- Use `sorted(usernames)` for large lists in production
- Built-in is fast, tested, and efficient

## 5. Common Mistakes / What Not to Do
- **Calling len() in key**: Use `key=len`, not `key=len()`—pass the function, not the result.
- **Wrong reverse placement**: `reverse=True` goes in `sorted()` call, not as separate operation.
- **Forgetting sign flips in tuple keys**: Use `-value` for descending within tuple, not `reverse=True`.
- **Writing manual sorts for production**: Use built-in `sorted()` instead of bubble/insertion sort implementations.
- **Confusing sorted() and .sort()**: Remember `sorted()` returns new list, `.sort()` returns None.

## 6. Open-Note Review
- `sorted()` returns new list, `.sort()` modifies in place
- `reverse=True` for descending order
- `key=len` for length sorting
- `key=lambda p: p[field]` for field access
- Tuple keys: `(-field1, field2)` for mixed order
- Use built-in `sorted()` in production

## 7. Final Takeaway
Master Python's built-in sorting tools—`sorted()` with `key`, `reverse=True`, and tuple keys for multi-criteria sorting—instead of implementing manual algorithms in production code.

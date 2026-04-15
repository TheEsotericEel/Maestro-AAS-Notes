# Matching Subproblems to Patterns

## 1. Concept: Algorithmic Patterns
> **Definition**: The practice of identifying standard, recurring computational structures (Map, Filter, Reduce, Sort, Search) within a unique problem.

Instead of inventing new algorithms from scratch, expert engineers act as **assemblers**, connecting pre-existing, optimized components. This concept is central to **Functional Programming**.

## 2. The "Why": The 80/20 Rule
Why use patterns?
1.  **Efficiency**: Standard patterns (like standard libraries) are optimized. Your custom loop might be $O(N^2)$, while the standard sort is $O(N \log N)$.
2.  **Readability**: `filter(is_even, nums)` is instantly readable. A 5-line `for` loop with an `if` statement requires cognitive decoding.
3.  **Reliability**: Common patterns have been tested for decades. Custom logic has not.

## 3. The "How": The Big Five
Most data processing problems can be solved by composing these five patterns:

### 1. Map (Transform)
*   **Action**: Apply a function to *every* item in a list.
*   **Result**: Same number of items, different values.
*   **Keywords**: "Convert", "Calculate for each", "Extract".

### 2. Filter (Select)
*   **Action**: Keep only items that meet a specific criteria.
*   **Result**: Fewer items (subset).
*   **Keywords**: "Find all that are...", "Remove", "Keep only".

### 3. Reduce (Accumulate/Aggregate)
*   **Action**: Combine all items into a single value.
*   **Result**: One value (Sum, Max, Min, Average).
*   **Keywords**: "Total", "Summary", "Average", "Count".

### 4. Search (Find)
*   **Action**: Stop at the first item that matches.
*   **Result**: One item (or None).
*   **Keywords**: "Is there a...", "Find the user...".

### 5. Sort (Order)
*   **Action**: Rearrange logic.
*   **Result**: Same items, different order.
*   **Keywords**: "Rank", "Top 10", "Cheapest first".

## 4. Examples: Pattern Recognition

### Problem: "Find the total price of all red items."
This is a compound pattern.
1.  **"Red items"** -> **Filter** (Keep only red).
2.  **"Total price"** -> **Reduce** (Sum the prices).

### Code Comparison

**❌ The Novice (Manual Loops)**
```python
total = 0
for item in items:
    if item.color == "red":
        total = total + item.price
```

**✅ The Pro (Pattern Composition)**
```python
# 1. Filter
red_items = [i for i in items if i.color == "red"]

# 2. Map (Implicit) & Reduce
total = sum(i.price for i in red_items)
```

## 5. Truth: Stop Inventing
If you are writing a `for` loop that iterates over a list and modifies a variable outside the loop, you are likely re-implementing **Map**, **Filter**, or **Reduce** poorly. Identify the pattern and use the standard tool.

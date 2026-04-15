# Comparing Two Solutions to the Same Problem

## 1. Introduction
The true power of Big O notation isn't just in analyzing a single piece of code—it's in evaluating and choosing between **multiple solutions** to the same problem. In software engineering, there are rarely "only one way" to do things, but there are definitely "better" ways.

In this document, we will tackle a single problem using two entirely different approaches and objectively compare them.

## 2. The Problem: Finding Duplicates
**Scenario**: You are given a list of user IDs. You need to write a function that returns `True` if there are any duplicate IDs in the list, and `False` otherwise.

Let's look at two ways to solve this.

### 2.1 Solution 1: The Naive Approach
A common first instinct is to simply compare every item in the list against every other item. 

```python
def has_duplicates_v1(user_ids):
    n = len(user_ids)
    # Compare every ID...
    for i in range(n):
        # ...to every other ID
        for j in range(n):
            # Make sure we don't compare the element to itself
            if i != j and user_ids[i] == user_ids[j]:
                return True
                
    return False
```

**Algorithm Analysis:**
- We have an outer loop running `n` times.
- We have an inner loop running `n` times.
- Therefore, for `n` items, we perform roughly `n * n` operations.
- **Time Complexity**: **O(n²)** (Quadratic Time)

**Pros**: Simple logic that is easy to write without knowing advanced data structures.
**Cons**: As the list grows, it becomes extremely inefficient.

### 2.2 Solution 2: The Optimized Approach
Instead of comparing everything to everything, what if we just keep a record of the IDs we have already seen as we go through the list once?

*Note: In Python, a `set` is a data structure where checking if an item exists (`if item in set`) happens in O(1) constant time.*

```python
def has_duplicates_v2(user_ids):
    seen = set()  
    
    # Go through the list exactly once
    for user_id in user_ids:
        # If we've seen it before, it's a duplicate!
        if user_id in seen:
            return True
            
        # Otherwise, add it to our record
        seen.add(user_id)
        
    return False
```

**Algorithm Analysis:**
- We have a single loop running `n` times.
- Checking `if user_id in seen` is O(1).
- Adding to the set `seen.add()` is O(1).
- **Time Complexity**: **O(n)** (Linear Time)

**Pros**: Extremely fast and scales gracefully with large inputs.
**Cons**: Requires understanding of Data Structures (like Sets). 

## 3. Comparing The Impact
Let's see why moving from **O(n²)** to **O(n)** matters when the data scales.

| Number of User IDs | Solution 1 (O(n²)) Operations | Solution 2 (O(n)) Operations |
|--------------------|-------------------------------|------------------------------|
| 10 users           | 100 operations                | 10 operations                |
| 100 users          | 10,000 operations             | 100 operations               |
| 1,000 users        | 1,000,000 operations          | 1,000 operations             |
| **100,000 users**  | **10 Billion operations! ⏳** | **100,000 operations 🚀**    |

For 100,000 users, Solution 1 could take minutes or hours to run. Solution 2 will finish in a fraction of a second.

## 4. The Time vs. Space Trade-off
Why wouldn't we *always* write the most highly-optimized solution right away? Often, to improve **time complexity** (speed), we must sacrifice **space complexity** (memory).

- **Solution 1** took O(n²) time but **O(1) space** (it used almost no extra memory, just a couple of variables).
- **Solution 2** sped up to O(n) time but used **O(n) space** (if the list has 1 million unique items, our `seen` set will also grow to hold 1 million items in memory!).

This tug-of-war between CPU speed and System Memory is one of the most fundamental trade-offs in computer science.

## 5. Summary
- It is perfectly normal to have multiple algorithms that solve the exact same problem.
- **Big O Notation** gives us a mathematical, objective way to choose the "better" algorithm.
- Improving Time Complexity is incredibly impactful for large datasets.
- Fast algorithms often require taking up more memory (The Time-Space Trade-Off).

### Next Steps
Now that you know how to compare solutions, we'll dive into ensuring our algorithms are safe and robust against errors.

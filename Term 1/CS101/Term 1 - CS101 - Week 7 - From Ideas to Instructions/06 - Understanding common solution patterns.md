# Standard Algorithmic Patterns

## 1. The Programmer's Toolbox

### What is it?
Experienced engineers rarely write algorithms from scratch. They recognize that a problem fits a known **Pattern** and implement that pattern.

### Why does it matter?
Patterns are tested, efficient, and readable. Using a standard pattern tells other engineers exactly what you are doing.

---

## 2. Core Patterns

### Pattern A: The Accumulator
**Goal**: Reduce a list of items to a single value (Sum, Count, Average, Concat).

**Mechanism**:
1.  **Initialize** a variable (the "Bucket") to zero or empty.
2.  **Iterate** through the list.
3.  **Update** the bucket with each item.

```python
# Summing prices
total = 0.0              # 1. Initialize
for price in prices:     # 2. Iterate
    total += price       # 3. Update
```

### Pattern B: The Flag (Sentinel)
**Goal**: Check if *any* or *all* items meet a condition.

**Mechanism**:
1.  **Initialize** a boolean flag (usually False).
2.  **Iterate**.
3.  **Set** flag to True if condition is met.
4.  **Break** (Optional optimization).

```python
# Is there a failing grade?
has_failed = False       # 1. Initialize
for grade in grades:
    if grade < 70:
        has_failed = True
        break            # Optimization: Found it, stop looking.
```

### Pattern C: The Filter
**Goal**: Create a subset of data.

**Mechanism**:
1.  **Initialize** an empty result list.
2.  **Iterate**.
3.  **Append** item to result IF condition is met.

```python
# Get passing grades
passing_grades = []      # 1. Initialize
for grade in grades:
    if grade >= 70:
        passing_grades.append(grade)
```

### Pattern D: The Lookup (Dictionary)
**Goal**: Map a "key" to a "value" without searching.

**Mechanism**:
1.  Define a Dictionary/Hash Map.
2.  Query by Key.

**Bad (Linear Search - O(N))**:
```python
if code == 'US': return 'United States'
elif code == 'CA': return 'Canada'
elif code == 'MX': return 'Mexico'
```

**Good (Direct Access - O(1))**:
```python
countries = {
    'US': 'United States',
    'CA': 'Canada', 
    'MX': 'Mexico'
}
return countries.get(code, "Unknown")
```

---

## 3. Selecting the Right Pattern

| Problem | Pattern |
| :--- | :--- |
| "Total up the..." | Accumulator |
| "Is there any..." | Flag |
| "Find all the..." | Filter |
| "Convert X to Y..." | Lookup |

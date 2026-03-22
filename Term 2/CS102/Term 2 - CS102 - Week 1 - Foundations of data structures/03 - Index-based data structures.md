# Index-Based Data Structures

## 1. Introduction
Index-based data structures use numbered positions (indices) to access and organize data. Think of them as rows of numbered mailboxes where each position holds a specific value.

## 2. The Core Concept: Numbered Positions
### The Mailbox Analogy
Imagine a row of numbered mailboxes in an apartment hallway:
- Each mailbox holds one person's mail (the value)
- Above each mailbox there's a number: 0, 1, 2, 3, ... (the index/position)
- When you want Alice's mail, you go straight to mailbox 3 and open it

In Python, lists and strings work the same way: `seq[3]` means "go to position 3 and give me what's there."

## 3. Zero-Based Indexing
### The Classic Off-by-One Trap
Python uses 0-based indexing, which means counting starts from 0, not 1.

```python
pets = ["cat", "dog", "hamster", "parrot"]
# index:   0       1         2         3

pets[0] → "cat"      # 1st pet
pets[1] → "dog"      # 2nd pet  
pets[2] → "hamster"  # 3rd pet
pets[3] → "parrot"   # 4th pet
```

**Key Rule**: The nth element is at index `n-1`.

## 4. Negative Indexing
### Counting from the End
Python allows negative indices that count from the right side, starting at -1.

```python
pets = ["cat", "dog", "hamster", "parrot"]
# index:    0      1        2         3
# neg:     -4     -3       -2        -1

pets[-1] → "parrot"    # last item
pets[-2] → "hamster"   # second from end
pets[-3] → "dog"       # third from end
pets[-4] → "cat"       # fourth from end
```

**Common Pattern**: `seq[-1]` is the idiomatic way to get the last element.

## 5. Sequential Access
### Visiting Items in Order
Sequential access means visiting each item one after another, like reading a book from left to right.

#### Method 1: Direct Value Access
```python
pets = ["cat", "dog", "hamster", "parrot"]

for pet in pets:
    print(pet)
# Output: cat, dog, hamster, parrot
```
- **Use case**: When you only need the values, not positions
- **Advantage**: Simple and readable

#### Method 2: Index-Based Access
```python
pets = ["cat", "dog", "hamster", "parrot"]

for i in range(len(pets)):
    print(i, pets[i])
# Output: 0 cat, 1 dog, 2 hamster, 3 parrot
```
- **Use case**: When you need both index and value
- **Advantage**: Explicit control over positions

#### Method 3: Enumerate (Preferred)
```python
pets = ["cat", "dog", "hamster", "parrot"]

for i, pet in enumerate(pets):
    print(i, pet)
# Output: 0 cat, 1 dog, 2 hamster, 3 parrot
```
- **Use case**: Clean way to get both index and value
- **Advantage**: Pythonic, efficient, and readable

## 6. Boundary Management
### Avoiding IndexError
Understanding list boundaries prevents the most common indexing error.

```python
levels = ["easy", "normal", "hard", "expert", "nightmare", "hell", "impossible"]
# indexes:    0        1        2        3          4          5        6

# Safe access patterns:
first = levels[0]                    # First element
last = levels[-1]                    # Last element  
last_by_len = levels[len(levels)-1]  # Last element using length

# Dangerous - will cause IndexError:
# levels[7]  # Index out of range!
```

**Golden Rule**: Valid indices are `0` through `len(seq) - 1`.

## 7. Practical Examples
### String Processing
```python
secret = "dragon"

for i, ch in enumerate(secret):
    print(f"{i} {ch}")
# Output: 0 d, 1 r, 2 a, 3 g, 4 o, 5 n
```

### List Manipulation
```python
scores = [85, 92, 78, 96, 88]

# Find positions of high scores
for i, score in enumerate(scores):
    if score >= 90:
        print(f"Position {i}: {score} (Excellent!)")
```

## 8. Performance Characteristics
### Time Complexity
- **Direct Access**: `seq[index]` → O(1) - Constant time
- **Sequential Access**: `for item in seq` → O(n) - Linear time
- **Length Access**: `len(seq)` → O(1) - Constant time

### Memory Layout
Index-based structures store elements in contiguous memory, enabling:
- Fast random access
- Predictable memory usage
- Cache-friendly operations

## 9. Common Patterns
### Reversing a Sequence
```python
# Method 1: Using negative indices
for i in range(len(seq)-1, -1, -1):
    print(seq[i])

# Method 2: Pythonic way
for item in reversed(seq):
    print(item)
```

### Finding Elements
```python
def find_position(seq, target):
    for i, item in enumerate(seq):
        if item == target:
            return i
    return -1  # Not found
```

## 10. Summary
Index-based data structures provide:
- **Direct Access**: Jump to any position instantly
- **Sequential Traversal**: Visit elements in order
- **Boundary Awareness**: Understand valid index ranges
- **Flexible Access**: Positive and negative indexing

> **Key Insight**: "Index → Slot → Value" - the fundamental mapping that makes index-based structures powerful and predictable.
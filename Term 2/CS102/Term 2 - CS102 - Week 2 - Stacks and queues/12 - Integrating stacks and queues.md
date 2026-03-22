# Integrating stacks and queues

## 1. Introduction
Sometimes we need to use both stacks and queues together. This lesson explores how to combine these data structures in real-world scenarios and Python implementations.

## 2. Queue of Stacks Concept
### Dragon Boat Ride Analogy
Imagine a line of visitors waiting for a dragon-boat ride 🐉:
- **The line**: People ride in the same order they arrived (FIFO - queue)
- **Treasure piles**: Each visitor keeps treasures on top, removes from top first (LIFO - stack)

### Conceptual Structure
```python
from collections import deque

# A queue where each element is a stack (list)
line = deque([
    ["coin", "gem"],      # Alice's stack (front of line)
    ["map"],              # Bob's stack
    ["ring", "potion"]    # Cara's stack (back of line)
])
```

## 3. Basic Operations
### Queue Operations (FIFO)
```python
from collections import deque

line = deque(["Alice", "Bob"])
line.append("Cara")        # Add to back
served = line.popleft()    # Remove from front
```

### Stack Operations (LIFO)
```python
treasures = ["coin", "gem"]
treasures.append("crown")  # Add to top
removed = treasures.pop()   # Remove from top
```

## 4. Combined Example
### Complete Dragon Boat Simulation
```python
from collections import deque

line = deque([
    ["coin", "gem"],      # Alice's treasures
    ["map"],              # Bob's treasures
    ["ring", "potion"]    # Cara's treasures
])

# One ride cycle
stack = line.popleft()    # Get front person's stack

if stack:
    removed = stack.pop()  # Remove top treasure
    print(f"Removed: {removed}")
    
    if stack:              # If still has treasures
        line.append(stack) # Go to back of line

print(f"Line after ride: {line}")
```

**Output**:
```
Removed: gem
Line after ride: deque([['map'], ['ring', 'potion'], ['coin']])
```

## 5. Multiple Cycles
### Two Ride Cycles
```python
from collections import deque

line = deque([
    ["coin", "gem"],      # Alice
    ["map"],              # Bob
    ["ring", "potion"]    # Cara
])

# Cycle 1
stack = line.popleft()
if stack:
    removed = stack.pop()
    print(f"Cycle 1 removed: {removed}")
    if stack:
        line.append(stack)

# Cycle 2
stack = line.popleft()
if stack:
    removed = stack.pop()
    print(f"Cycle 2 removed: {removed}")
    if stack:
        line.append(stack)

print(f"Final line: {line}")
```

**Output**:
```
Cycle 1 removed: gem
Cycle 1 removed: map
Final line: deque([['ring', 'potion'], ['coin']])
```

## 6. Choosing the Right Structure
### Decision Rules
- **Queue**: Process in same order as arrival
- **Stack**: Always work with most recent item first

### Real-World Scenarios
**Scenario 1**: Support tickets (oldest handled first) → **Queue**
**Scenario 2**: Undo feature (most recent undone first) → **Stack**

### Restaurant Example
- **Orders waiting**: Queue (cook in order received)
- **Plates on chef's arm**: Stack (serve from top)

## 7. Quick Reference
| Structure | Order | Python | Use Case |
|-----------|-------|--------|----------|
| Queue | FIFO | `deque.append()`, `deque.popleft()` | Processing in arrival order |
| Stack | LIFO | `list.append()`, `list.pop()` | Working with newest first |

## 8. Summary
### Key Concepts
- **Queue of stacks**: Each queue element is itself a stack
- **FIFO between elements**: Queue determines processing order
- **LIFO within elements**: Stack determines internal processing

### Common Patterns
- **Service lines with individual items**: Queue of people, each with a stack of items
- **Task processing**: Queue of tasks, each with a stack of sub-tasks
- **Resource management**: Queue of resources, each with a stack of operations

### Mastery Checklist
- ✅ Understand when to use queue vs stack
- ✅ Implement queue of stacks in Python
- ✅ Process combined structures correctly
- ✅ Apply to real-world scenarios
- ✅ Choose appropriate structures for new problems

> **Key Insight**: "Queues and stacks often work together - queues manage the 'who goes next' decision, while stacks manage the 'what to do within each item' decision."
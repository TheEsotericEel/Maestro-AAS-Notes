# Implementing queues with deque

## 1. Introduction
You already learned about queues using Python lists. Now we'll learn a better tool: `deque` from the `collections` module.

## 2. Why Use Deque?
Imagine a line for a new roller coaster . With lists, when someone leaves the front, everyone behind has to shift forward - this is slow! Deque is designed for efficient queue operations.

## 3. Setting Up Deque
```python
from collections import deque

# Create an empty deque queue
line = deque()
print(f"Empty deque: {line}")
```

## 4. Enqueue with Deque
Adding people to the back of the line:
```python
from collections import deque

line = deque()
line.append("Alice")
print(f"After Alice: {line}")

line.append("Bob")
print(f"After Bob: {line}")

line.append("Charlie")
print(f"After Charlie: {line}")
```

## 5. Dequeue with Deque
Removing people from the front of the line:
```python
from collections import deque

line = deque(["Alice", "Bob", "Charlie"])
print(f"Initial: {line}")

served = line.popleft()
print(f"Served: {served}")
print(f"Remaining: {line}")

served = line.popleft()
print(f"Served: {served}")
print(f"Remaining: {line}")
```

## 6. Complete Example
```python
from collections import deque

line = deque()

# People join the line
line.append("Tom")
line.append("Jerry")
line.append("Spike")
print("Before serving:", line)

# Serve people in order
first = line.popleft()
second = line.popleft()

print("Served:", first, "&", second)
print("After serving:", line)
```

## 7. Performance Comparison
| Operation | List Method | Time | Deque Method | Time |
|-----------|-------------|------|--------------|------|
| Enqueue | `append(item)` | O(1) | `append(item)` | O(1) |
| Dequeue | `pop(0)` | O(n) | `popleft()` | O(1) |

**Key Point**: Deque is much faster for dequeue because it doesn't need to shift all remaining items.

## 8. Quick Checks
- What do you import? → `from collections import deque`
- How do you enqueue? → `append(item)`
- How do you dequeue? → `popleft()`
- Why is deque better? → O(1) dequeue vs O(n) with lists

## 9. Summary
- **Import**: `from collections import deque`
- **Create**: `line = deque()`
- **Enqueue**: `line.append(item)`
- **Dequeue**: `line.popleft()`
- **Advantage**: Much faster dequeue operations

> **Key Insight**: "Deque gives you O(1) dequeue operations, making it the right choice for high-performance queues."

### Mastery Checklist
- Import deque from collections
- Create empty deque queue
- Use append() for enqueue
- Use popleft() for dequeue
- Understand performance benefits
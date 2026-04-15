# Combined Array Operations in Sequence

## 1. Introduction
Combined array operations involve performing multiple actions on the same list in a deliberate order. This lesson covers how to chain operations like accessing, updating, and removing elements while tracking index shifts and returned values.

## 2. Core Scenario (Bench Coach Analogy 🏀)
We manage a bench of players using one function:
- **Access**: Read a player by index
- **Update**: Modify a player in place
- **Remove**: Pop a player and capture the removed value

### Example List
```python
players = ["Ana", "Ben", "Cara", "Dan", "Eli"]
# indexes:    0      1      2      3      4
```

## 3. The manage_bench Function
### Desired Steps (in order)
1) Access the first player (read-only)
2) Update the last player to "SUB"
3) Remove the middle player with `pop()`
4) Return the removed player and the new length of the list

### Implementation
```python
def manage_bench(players):
    first_player = players[0]          # access
    players[-1] = "SUB"                # update last
    mid_index = len(players) // 2      # middle index (odd length)
    removed_player = players.pop(mid_index)  # remove middle
    return removed_player, len(players)      # tuple return

players = ["Ana", "Ben", "Cara", "Dan", "Eli"]
removed, new_len = manage_bench(players)
# removed -> "Cara"
# new_len -> 4
# players -> ["Ana", "Ben", "Dan", "SUB"]
```

## 4. Index Shifting After pop()
Removing from the middle shifts everything to the left.
```python
nums = [10, 20, 30, 40, 50]
nums.pop(1)       # removes 20
# nums is now [10, 30, 40, 50]
# index 2 now holds 40 (previously 3)
```

## 5. Tuple Returns & Unpacking
Functions can return multiple values as a tuple, then unpack them into variables.
```python
removed_player, new_length = manage_bench(players)
```
- Left side variables line up with tuple positions.
- Avoid assigning the whole tuple to one variable when you need separate values.

## 6. Common Patterns
- **Access → Update → Remove**: Perform operations in the required order to avoid index surprises.
- **Middle index**: `mid_index = len(lst) // 2`
- **Pop semantics**: `pop()` returns the removed element and mutates the list.
- **Index shift awareness**: After `pop(i)`, all elements to the right move left by one.

## 7. Quick Checks
- What does `pop()` return? → The removed element.
- What happens to indices after `pop(0)`? → All elements shift left; former index 1 becomes index 0.
- How do you unpack a tuple return? → `a, b = fn()`.

## 8. Summary
In combined operations, order matters: read, then update, then remove. Track shifting indices after removals, and use tuple returns plus unpacking to surface useful results while mutating the original list.

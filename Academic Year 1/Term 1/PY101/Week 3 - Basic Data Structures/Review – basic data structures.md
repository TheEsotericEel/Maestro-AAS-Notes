# Review – basic data structures

## 📚 Week 3 Summary
This week we moved from simple variables to **Collections**.

### 1. Sequences (Strings & Lists)
- **Ordered**: Position 0, 1, 2...
- **Indexing**: `[i]` to get one.
- **Slicing**: `[start:stop]` to get many.

### 2. Mutability
- **Strings**: Immutable. `s.upper()` returns a *new* string.
- **Lists**: Mutable. `L.append(x)` changes *that* list.

### 3. Dictionaries (Mappings)
- **Unordered** (conceptually).
- **Key-Value**: Access by Label, not position.
- **Fast**: Looking up a key is instant O(1).

### 4. Common Patterns
- **Filter**: `[x for x in L if check(x)]` (or loop + append).
- **Accumulate**: Loop + `total += x`.
- **Search**: `if x in collection:`.

## 🛑 Checkpoint
Can you answer these?

1. What is the difference between `list.append(x)` and `list.extend(x)`?
2. If `a = [1, 2]` and `b = a`, does changing `b` change `a`?
3. How do you safely get a value from a dictionary that might be missing?
4. What happens if you try to change a character in a string: `s[0] = "A"`?

## 🔗 Next Steps
Practice the **Challenge**. Data structures are the building blocks of all complex programs. Master them, and you can model anything.
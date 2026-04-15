# How Searching Works with Simple Examples

## 1. Lesson Focus
Understanding what a search is, how it works step by step, and how to recognize when a process is (and isn't) a search.

## 2. Core Concepts
**Search**: The process of checking items one by one in a collection until you either find the target or run out of items.

**Target**: The specific item you're trying to find in the collection.

**Collection**: The data structure (list, array, etc.) you're searching through.

**Current Item**: The item being checked at each step of the search.

## 3. Key Details to Remember
- A search involves step-by-step checking of items in order
- The target is what you're looking for, not the collection
- Direct access (jumping to a known position) is not a search
- Searching stops when the target is found or the collection is exhausted

## 4. How It Works
**Linear Search Process**:
1. Start at the first item (index 0)
2. Check if current item equals target
3. If yes, stop and report found
4. If no, move to next item
5. Repeat until target found or end of collection

## 5. Examples

### Example 1: Key Rack Analogy
```
Key rack: [slot0, slot1, slot2, slot3, slot4]
Target: 🗝️ key

Process:
- Check slot0: is it 🗝️? No
- Check slot1: is it 🗝️? No
- Check slot2: is it 🗝️? Yes → found
```

### Example 2: Python Linear Search
```python
keys = ["🚗", "🏠", "🗝️", "🏢", "📦"]
target = "🗝️"

for i in range(len(keys)):
    item = keys[i]
    print(f"Checking slot {i}: {item}")
    if item == target:
        print("Found the key at slot", i)
        break
```

**Trace output:**
```
Checking slot 0: 🚗
Checking slot 1: 🏠
Checking slot 2: 🗝️
Found the key at slot 2
```

### Example 3: Word Search
```python
words = ["cat", "dog", "eel", "fox", "yak"]
target = "eel"

for i in range(len(words)):
    item = words[i]
    print(f"Checking index {i}: {item}")
    if item == target:
        print("Found the key at slot", i)
        break
```

## 6. What Is Not a Search
**Direct Access**: Going straight to a known position without checking other items.

Examples:
- Always grabbing key from hook 2 (not a search)
- Typing site name in password manager (not a search)
- Opening "notes.txt" directly (not a search)
- Checking watch for time (not a search)

## 7. Common Mistakes / What Not to Do
- **Confusing target with collection**: The target is the specific item you want, not the whole collection.
- **Thinking direct access is search**: Jumping to a known position is not searching—it's direct lookup.
- **Forgetting step-by-step checking**: A search requires checking items in order, not jumping directly.

## 8. Open-Note Review
- Search = check items one by one until target found or exhausted
- Target = specific item being sought
- Collection = data structure being searched
- Direct access ≠ search
- Linear search complexity: O(n)

## 9. Final Takeaway
A search is defined by step-by-step checking of items in order to find a target—direct access to known positions is not a search.

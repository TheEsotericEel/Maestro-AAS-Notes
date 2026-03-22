# Week 3 Bonus Information - Basic Data Structures

> **Purpose**: Supplementary definitions, examples, and clarifications for Week 3 concepts

---

## String Indexing - Complete Reference

### Positive Indexing (Left to Right)
```py
text = "Python"
# Index:  0  1  2  3  4  5
#         P  y  t  h  o  n

print(text[0])              # P
print(text[3])              # h
print(text[5])              # n
print(text[6])              # ❌ IndexError (out of range)
```

### Negative Indexing (Right to Left)
```py
text = "Python"
# Index:  -6 -5 -4 -3 -2 -1
#          P  y  t  h  o  n

print(text[-1])             # n (last character)
print(text[-3])             # h
print(text[-6])             # P (first character)
```

### Index Bounds
```py
text = "Hello"
# Valid indices: 0 to 4 (or -5 to -1)
# Length: 5
# Last valid index: len(text) - 1 = 4
```

---

## String Slicing - Complete Guide

### Basic Slice: `[start:stop]`
```py
text = "Python"
# Index:  0  1  2  3  4  5
#         P  y  t  h  o  n

text[0:2]                   # "Py" (includes 0, excludes 2)
text[2:6]                   # "thon" (includes 2, excludes 6)
text[1:4]                   # "yth" (includes 1, excludes 4)
```

### Open-Ended Slices
```py
text = "Python"

text[:3]                    # "Pyt" (from start to index 3)
text[3:]                    # "hon" (from index 3 to end)
text[:]                     # "Python" (entire string - copy)
```

### Slice with Step: `[start:stop:step]`
```py
text = "Python"

text[0:6:2]                 # "Pto" (every 2nd character)
text[::2]                    # "Pto" (same, from start to end)
text[1::2]                   # "yhn" (every 2nd, starting at 1)
```

### Negative Step (Reverse)
```py
text = "Python"

text[::-1]                  # "nohtyP" (reverse entire string)
text[5:0:-1]                 # "nohty" (reverse from 5 to 0)
text[4::-1]                  # "ohtyP" (reverse from 4 to start)
```

### Slice Rules Summary
- **Includes** `start` index
- **Excludes** `stop` index
- **Step** determines direction and spacing
- **Negative step** goes backwards

---

## String Methods - Quick Reference

### strip() - Remove Whitespace
```py
text = "  Hello  "
text.strip()                 # "Hello" (removes leading/trailing spaces)

stars = "***text***"
stars.strip("*")             # "text" (removes leading/trailing *)
```

### lower() - Convert to Lowercase
```py
text = "Hello World"
text.lower()                # "hello world" (returns new string)
# Original unchanged: text is still "Hello World"
```

### replace() - Replace Substrings
```py
text = "one two one"
text.replace("one", "three") # "three two three" (all occurrences)
text.replace("one", "three", 1)  # "three two one" (only first)
```

### find() - Locate Substring
```py
text = "Hello World"
text.find("World")          # 6 (index where "World" starts)
text.find("Python")         # -1 (not found)
text.find("l")              # 2 (first occurrence)
```

### split() - Break into List
```py
text = "apple,banana,cherry"
text.split(",")             # ["apple", "banana", "cherry"]

text = "one  two   three"
text.split()                # ["one", "two", "three"] (splits on whitespace)

text = "a,,b"
text.split(",")             # ["a", "", "b"] (empty string between commas)
```

### join() - Combine List into String
```py
words = ["apple", "banana", "cherry"]
",".join(words)             # "apple,banana,cherry"
" ".join(words)             # "apple banana cherry"
"-".join(words)             # "apple-banana-cherry"
```

### Method Chaining
```py
text = "  Hello, World  "
text.strip().lower().replace(",", "")  # "hello world"
# Process: strip → lower → replace
```

---

## Lists - Creation Patterns

### List Literals
```py
numbers = [1, 2, 3, 4, 5]
fruits = ["apple", "banana", "cherry"]
mixed = [1, "hello", 3.14, True]
empty = []                  # Empty list
```

### From range()
```py
numbers = list(range(5))     # [0, 1, 2, 3, 4]
evens = list(range(2, 11, 2))  # [2, 4, 6, 8, 10]
```

### List of Lists
```py
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
# Access: matrix[0][1] = 2
```

### List Repetition
```py
zeros = [0] * 5             # [0, 0, 0, 0, 0]
pattern = ["a", "b"] * 3    # ["a", "b", "a", "b", "a", "b"]
```

---

## List Indexing and Slicing

### Indexing (Same as Strings)
```py
items = [10, 20, 30, 40]
items[0]                    # 10
items[-1]                   # 40 (last element)
items[4]                    # ❌ IndexError
```

### Slicing (Creates New List)
```py
items = [10, 20, 30, 40, 50]
items[1:4]                  # [20, 30, 40] (new list)
items[:3]                   # [10, 20, 30]
items[2:]                   # [30, 40, 50]
items[::2]                  # [10, 30, 50] (every 2nd)
```

### Modifying by Index
```py
items = [10, 20, 30]
items[1] = 25               # [10, 25, 30] (modifies original)
```

### Slicing vs Indexing
```py
items = [10, 20, 30]

items[1]                    # 20 (single element, int)
items[1:2]                  # [20] (list with one element)
```

---

## List Methods - Complete Reference

### Adding Items

```py
# append() - Add one item to end
items = [1, 2, 3]
items.append(4)             # [1, 2, 3, 4]

# extend() - Add multiple items
items = [1, 2, 3]
items.extend([4, 5])         # [1, 2, 3, 4, 5]

# insert() - Insert at position
items = [1, 2, 3]
items.insert(1, 99)          # [1, 99, 2, 3] (inserts at index 1)
```

### Removing Items

```py
# pop() - Remove by position (returns value)
items = [1, 2, 3, 4]
value = items.pop()          # value = 4, items = [1, 2, 3]
value = items.pop(0)         # value = 1, items = [2, 3]

# remove() - Remove by value (first occurrence)
items = [1, 2, 3, 2]
items.remove(2)             # [1, 3, 2] (removes first 2)
items.remove(5)             # ❌ ValueError (not found)
```

### Finding Items

```py
# index() - Find position
items = [10, 20, 30, 20]
items.index(20)             # 1 (first occurrence)
items.index(50)             # ❌ ValueError (not found)

# count() - Count occurrences
items = [1, 2, 2, 3, 2]
items.count(2)              # 3
items.count(5)              # 0
```

### Reordering

```py
# sort() - Sort in place
items = [3, 1, 4, 2]
items.sort()                # [1, 2, 3, 4] (modifies original)
items.sort(reverse=True)    # [4, 3, 2, 1]

# reverse() - Reverse order
items = [1, 2, 3]
items.reverse()             # [3, 2, 1] (modifies original)
```

### sorted() vs sort()

```py
items = [3, 1, 4, 2]

# sorted() - Returns new list
new_list = sorted(items)     # [1, 2, 3, 4]
# items unchanged: [3, 1, 4, 2]

# sort() - Modifies original
items.sort()                 # items = [1, 2, 3, 4]
```

---

## List Iteration Patterns

### Pattern 1: Iterate Over Values
```py
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
    print(fruit)             # apple, banana, cherry
```

### Pattern 2: Iterate with Index
```py
fruits = ["apple", "banana", "cherry"]
for i in range(len(fruits)):
    print(i, fruits[i])      # 0 apple, 1 banana, 2 cherry
```

### Pattern 3: Filter (Build New List)
```py
numbers = [1, 2, 3, 4, 5, 6]
evens = []
for n in numbers:
    if n % 2 == 0:
        evens.append(n)      # [2, 4, 6]
```

### Pattern 4: Transform (Build New List)
```py
numbers = [1, 2, 3]
squares = []
for n in numbers:
    squares.append(n * n)    # [1, 4, 9]
```

### Pattern 5: Accumulate
```py
numbers = [10, 20, 30]
total = 0
for n in numbers:
    total = total + n        # total = 60
```

---

## Dictionaries - Complete Guide

### Creating Dictionaries
```py
# Literal syntax
person = {"name": "Alice", "age": 30, "city": "NYC"}

# Empty dictionary
empty = {}

# From key-value pairs
data = dict(name="Bob", age=25)  # {"name": "Bob", "age": 25}
```

### Accessing Values
```py
person = {"name": "Alice", "age": 30}

person["name"]               # "Alice"
person["age"]                # 30
person["email"]              # ❌ KeyError (key doesn't exist)
```

### Safe Access with get()
```py
person = {"name": "Alice", "age": 30}

person.get("name")           # "Alice"
person.get("email")          # None (key doesn't exist)
person.get("email", "N/A")   # "N/A" (default value)
```

### Adding/Updating
```py
person = {"name": "Alice"}

person["age"] = 30           # Add new key
person["name"] = "Bob"       # Update existing key
person["city"] = "NYC"       # Add another key
```

### Checking Keys
```py
person = {"name": "Alice", "age": 30}

"name" in person             # True
"email" in person            # False
```

---

## Dictionary Iteration Patterns

### Pattern 1: Iterate Over Keys (Default)
```py
scores = {"Alice": 85, "Bob": 92, "Carol": 78}
for name in scores:          # Iterates over keys
    print(name, scores[name])
# Alice 85
# Bob 92
# Carol 78
```

### Pattern 2: Iterate Over Keys (Explicit)
```py
scores = {"Alice": 85, "Bob": 92}
for name in scores.keys():
    print(name)              # Alice, Bob
```

### Pattern 3: Iterate Over Values
```py
scores = {"Alice": 85, "Bob": 92, "Carol": 78}
for score in scores.values():
    print(score)             # 85, 92, 78
```

### Pattern 4: Iterate Over Items (Key-Value Pairs)
```py
scores = {"Alice": 85, "Bob": 92}
for name, score in scores.items():
    print(f"{name}: {score}")
# Alice: 85
# Bob: 92
```

### Pattern 5: Filter by Value
```py
scores = {"Alice": 85, "Bob": 92, "Carol": 78}
for name, score in scores.items():
    if score >= 80:
        print(name)          # Alice, Bob
```

---

## Copy vs Alias - Deep Dive

### Alias (Same Object)
```py
original = [1, 2, 3]
alias = original             # Alias (same object)

original.append(4)
print(alias)                 # [1, 2, 3, 4] (both changed)
```

### Shallow Copy (New Object)
```py
original = [1, 2, 3]
copy = original[:]           # Shallow copy (new list)

original.append(4)
print(original)              # [1, 2, 3, 4]
print(copy)                  # [1, 2, 3] (unchanged)
```

### Copy Methods for Lists
```py
original = [1, 2, 3]

# Method 1: Slice
copy1 = original[:]

# Method 2: list() constructor
copy2 = list(original)

# Method 3: .copy() method
copy3 = original.copy()
```

### Copy Methods for Dictionaries
```py
original = {"a": 1, "b": 2}

# Method 1: dict() constructor
copy1 = dict(original)

# Method 2: .copy() method
copy2 = original.copy()
```

### Testing: Alias vs Copy
```py
# Test: Modify one, check the other
original = [1, 2, 3]
copy = original[:]           # Copy

original.append(4)
if copy == [1, 2, 3]:
    print("It's a copy")     # ✅ Prints this
else:
    print("It's an alias")
```

---

## Nested Structures - Access Patterns

### Nested Lists
```py
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
# Access: matrix[row][column]

matrix[0][1]                 # 2 (row 0, column 1)
matrix[2][0]                 # 7 (row 2, column 0)
```

### Nested Dictionaries
```py
person = {
    "name": "Alice",
    "address": {
        "street": "123 Main",
        "city": "NYC"
    }
}

person["name"]               # "Alice"
person["address"]["city"]    # "NYC"
```

### Mixed Structures
```py
data = {
    "students": ["Alice", "Bob"],
    "scores": [85, 92]
}

data["students"][0]         # "Alice" (dict → list → index)
data["scores"][1]           # 92
```

### Safe Nested Access
```py
person = {"name": "Alice"}

# Unsafe (crashes if key missing)
age = person["address"]["city"]  # ❌ KeyError

# Safe (returns None if missing)
age = person.get("address", {}).get("city")  # None
```

---

## Mutability - Lists vs Strings

### Strings are Immutable
```py
text = "Hello"
text[0] = "h"               # ❌ TypeError (can't modify string)
# Must create new string:
text = "h" + text[1:]       # "hello" (new string)
```

### Lists are Mutable
```py
items = [1, 2, 3]
items[0] = 10               # ✅ [10, 2, 3] (modified in place)
items.append(4)              # ✅ [10, 2, 3, 4]
```

### Dictionaries are Mutable
```py
person = {"name": "Alice"}
person["age"] = 30          # ✅ Add new key
person["name"] = "Bob"      # ✅ Modify existing key
```

---

## Common List Operations

### Finding Maximum/Minimum
```py
numbers = [10, 5, 20, 15]
max(numbers)                # 20
min(numbers)                # 5
```

### Sum
```py
numbers = [1, 2, 3, 4]
sum(numbers)                # 10
```

### Length
```py
items = [1, 2, 3, 4, 5]
len(items)                  # 5
```

### Membership Check
```py
fruits = ["apple", "banana", "cherry"]
"apple" in fruits           # True
"grape" in fruits           # False
```

---

## String vs List Comparison

| Feature | String | List |
|---------|--------|------|
| Indexing | ✅ `text[0]` | ✅ `items[0]` |
| Slicing | ✅ `text[1:3]` | ✅ `items[1:3]` |
| Iteration | ✅ `for char in text` | ✅ `for item in items` |
| Length | ✅ `len(text)` | ✅ `len(items)` |
| Membership | ✅ `"a" in text` | ✅ `item in items` |
| Mutable | ❌ Immutable | ✅ Mutable |
| Methods | `.upper()`, `.split()` | `.append()`, `.sort()` |

---

## Dictionary Methods Summary

### keys(), values(), items()
```py
data = {"a": 1, "b": 2, "c": 3}

list(data.keys())            # ["a", "b", "c"]
list(data.values())          # [1, 2, 3]
list(data.items())           # [("a", 1), ("b", 2), ("c", 3)]
```

### get() with Default
```py
scores = {"Alice": 85}

scores.get("Alice")          # 85
scores.get("Bob", 0)         # 0 (default for missing key)
```

### pop() - Remove and Return
```py
data = {"a": 1, "b": 2}
value = data.pop("a")        # value = 1, data = {"b": 2}
value = data.pop("c", 0)     # value = 0 (default, key doesn't exist)
```

---

## List Comprehension Preview (Concept)

### Traditional Loop
```py
numbers = [1, 2, 3, 4, 5]
squares = []
for n in numbers:
    squares.append(n * n)    # [1, 4, 9, 16, 25]
```

### List Comprehension (More Concise)
```py
numbers = [1, 2, 3, 4, 5]
squares = [n * n for n in numbers]  # [1, 4, 9, 16, 25]
```

*Note: Full coverage in later weeks, but good to recognize the pattern*

---

## Common Patterns

### Pattern 1: Build List from Input
```py
numbers = []
for i in range(5):
    num = int(input("Enter number: "))
    numbers.append(num)
```

### Pattern 2: Count Occurrences
```py
items = ["a", "b", "a", "c", "a"]
count = items.count("a")    # 3
```

### Pattern 3: Find Maximum Value in Dictionary
```py
scores = {"Alice": 85, "Bob": 92, "Carol": 78}
max_score = max(scores.values())  # 92
```

### Pattern 4: Reverse a List
```py
items = [1, 2, 3]
items.reverse()             # [3, 2, 1] (modifies original)
reversed_items = items[::-1]  # [1, 2, 3] (new list, original unchanged)
```

---

## Error Handling for Data Structures

### IndexError (List/String)
```py
items = [1, 2, 3]
items[10]                    # ❌ IndexError

# Safe access:
if len(items) > 10:
    value = items[10]
```

### KeyError (Dictionary)
```py
data = {"a": 1}
data["b"]                    # ❌ KeyError

# Safe access:
value = data.get("b", 0)     # 0 (default)
```

### ValueError (List Methods)
```py
items = [1, 2, 3]
items.remove(5)              # ❌ ValueError (not found)

# Safe removal:
if 5 in items:
    items.remove(5)
```

---

## Week 3 Mastery Checklist

Before moving to later weeks, you should be able to:

- [ ] Index and slice strings
- [ ] Use string methods (strip, lower, replace, find, split, join)
- [ ] Create lists with literals and from range()
- [ ] Index and slice lists
- [ ] Modify list elements by index
- [ ] Use list methods (append, extend, insert, pop, remove, sort, etc.)
- [ ] Iterate over lists with for loops
- [ ] Filter and transform lists
- [ ] Create dictionaries with key-value pairs
- [ ] Access dictionary values by key
- [ ] Use get() for safe access
- [ ] Iterate over dictionary keys, values, and items
- [ ] Distinguish between alias and copy
- [ ] Create shallow copies of lists and dictionaries
- [ ] Access nested structures (lists in lists, dicts in dicts)
- [ ] Use safe access patterns for nested data

---

*End of Week 3 Bonus Information*

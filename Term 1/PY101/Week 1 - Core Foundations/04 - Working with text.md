# Lesson 04: Working with Text (Strings)

## 🎯 End Goal
To manipulate text data fundamentally. You will learn to access individual characters (Indexing), extract subsections (Slicing), and transform text using built-in methods.

## 🧠 Core Concepts

### 1. The String as a Sequence
A String (`str`) is not a single atomic object. It is an **ordered sequence of characters**.
*   **Ordered**: The order clearly matters. "Cat" is not "Act".
*   **Indexed**: Every character has a numbered position, starting at **0**.

### 2. Zero-Based Indexing
In Computer Science, we start counting at 0, not 1.
*   **Why**: The index represents the **offset** (distance) from the beginning. The first item is 0 steps away.

| P | y | t | h | o | n |
| :---: | :---: | :---: | :---: | :---: | :---: |
| 0 | 1 | 2 | 3 | 4 | 5 |

### 3. Immutability
Strings in Python are **immutable**.
*   **Meaning**: Once created, you cannot change a character *inside* it.
*   **Correction**: You must create a *new* string if you want to make a change.
    *   ❌ `s[0] = "X"` (Error)
    *   ✅ `s = "X" + s[1:]` (Create new string)

## 🛠️ The Toolkit

### Accessing Characters (Indexing)
Use square brackets `[]` to ask for a specific character.
```python
text = "Python"
first = text[0]  # 'P'
last = text[-1]  # 'n' (Negative starts from end!)
```

### Extracting Substrings (Slicing)
Use the colon `:` to specify a range `[start : stop]`.
*   **Rule**: Inclusive of `start`, EXCLusive of `stop`. "Start at start, go up to (but not including) stop."
```python
text = "Python"
part = text[0:2] # 'Py' (Indices 0, 1. Stop before 2)
```

### Text Methods
Strings have built-in functions attached to them called **methods**. You access them with dot notation `.`.
*   `.upper()`: Converts to ALL CAPS.
*   `.lower()`: Converts to lowercase.
*   `.title()`: Capitalizes First Letter Of Each Word.

## 📝 Examples

### Basic Manipulation
```python
name = "ada lovelace"

# Uppercase
print(name.upper()) # "ADA LOVELACE"

# Capitalize
print(name.title()) # "Ada Lovelace"
```

### The "Slice"
```python
filename = "report.txt"

# Get just the name "report"
# Go from start (0) up to index 6
print(filename[0:6]) # "report"

# Get the extension ".txt"
# Go from index -4 to the end
print(filename[-4:]) # ".txt"
```

## ⚡ Associations
*   **`[]`**: The Index Operator (The "Grabber").
*   **`:`**: The Range Operator (The "Slicer").
*   **Zero Index**: "How far from the start?"
*   **Negative Index**: "How far from the end?"

## ⚠️ Traps and Pitfalls

| Mistake | Code | Error Type | Explanation |
| :--- | :--- | :--- | :--- |
| **Index Out of Range** | `s = "Hi"`<br>`print(s[5])` | `IndexError` | You tried to grab index 5 from a string that only goes up to 1. |
| **Mutation Attempt** | `s[0] = "X"` | `TypeError` | Strings are immutable. "Item assignment" is forbidden. |
| **Off-by-One Error** | `s[0:3]` | `(Logic Error)` | You wanted indices 0, 1, 2, 3? Too bad. Python stops *before* the second number. It gives you 0, 1, 2. |

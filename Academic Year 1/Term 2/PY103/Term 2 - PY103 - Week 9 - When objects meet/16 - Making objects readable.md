# Making Objects Readable

## 1. Lesson Focus
The `__str__` special method allows objects to provide a human-readable string representation. Instead of Python's default `<__main__.ClassName object at 0x...>` format, `print(obj)` displays a friendly, descriptive message.

## 2. Core Concepts
- **Default Object Representation**: Python's default way of showing objects includes the class name and memory address (e.g., `<__main__.Pet object at 0x7f9c2b8d2f10>`). Useful for Python, not humans.
- **`__str__` Method**: A special method that returns a human-friendly string representation of an object. Called by `print()` and `str()`.
- **`__repr__` Method**: A special method for developer/debugging representation (more technical). If not defined, Python falls back to the default format.
- **Special Methods**: Methods surrounded by double underscores (dunder methods) that Python calls automatically in specific situations.

## 3. Key Details to Remember
- `__str__` must return a string
- `__str__` is called automatically by `print(obj)` and `str(obj)`
- Method name requires exactly two underscores before and after: `__str__` (not `__str_`)
- `__str__` is for human-readable output
- `__repr__` is for developer/debugging output
- If `__str__` is not defined, Python uses the default representation

## 4. How It Works

### Without __str__ (Default Behavior)
```python
class Pet:
    def __init__(self, name, age):
        self.name = name
        self.age = age

pet = Pet("Buddy", 3)
print(pet)  # Output: <__main__.Pet object at 0x14e4e78>
```

### With __str__ (Custom Representation)
```python
class Pet:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def __str__(self):
        return f"{self.name} ({self.age} years old)"

pet = Pet("Buddy", 3)
print(pet)  # Output: Buddy (3 years old)
```

## 5. Examples

### Example 1: Pet Class with __str__
```python
class Pet:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def __str__(self):
        return f"{self.name} ({self.age} years old)"


# ---- main ----
pet = Pet("Buddy", 3)
print(pet)  # Output: Buddy (3 years old)
```

### Example 2: Book Class with __str__
```python
class Book:
    def __init__(self, title, author):
        self.title = title
        self.author = author

    def __str__(self):
        return f"{self.title} by {self.author}"


# ---- main ----
book = Book("1984", "George Orwell")
print(book)  # Output: 1984 by George Orwell
```

### Example 3: Multiple Objects in a List
```python
class Pet:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def __str__(self):
        return f"{self.name} ({self.age} years old)"


# ---- main ----
pets = [
    Pet("Buddy", 3),
    Pet("Whiskers", 5),
    Pet("Rex", 2)
]

for pet in pets:
    print(pet)
# Output:
# Buddy (3 years old)
# Whiskers (5 years old)
# Rex (2 years old)
```

## 6. Common Mistakes / What Not to Do
- **Incorrect underscore count**: Writing `__str_` (missing trailing underscore) instead of `__str__`. Python requires exactly two underscores on each side.
- **Forgetting to return a string**: The method must return a string, not print it directly.
- **Returning non-string values**: `__str__` must return a string; returning other types causes errors.
- **Confusing __str__ with __repr__**: `__str__` is for human-readable output, `__repr__` is for developer/debugging output.

## 7. Open-Note Review
- `__str__` provides human-readable string representation
- Called automatically by `print(obj)` and `str(obj)`
- Must return a string
- Exact syntax: `def __str__(self):` (two underscores on each side)
- Replaces default `<__main__.ClassName object at 0x...>` format
- `__str__` = human-friendly, `__repr__` = developer/debugging

## 8. Final Takeaway
Define `__str__` in a class to provide a human-readable string representation. When `print(obj)` is called, Python uses the string returned by `__str__` instead of the default memory address format, making object output clear and useful for humans.

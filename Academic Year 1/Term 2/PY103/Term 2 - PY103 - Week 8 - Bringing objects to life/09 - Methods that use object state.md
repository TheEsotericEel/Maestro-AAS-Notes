# Methods that Use Object State

## 1. Lesson Focus
Shows how to write **read-only instance methods** that read an object's attributes via `self` and return or print information based on the current state, without modifying any attributes.

---

## 2. Core Concepts

### Constructor vs Read-Only Methods
| Method Type | Purpose | Modifies State? |
|-------------|---------|---------------|
| `__init__` | Set up initial state | Yes (creates attributes) |
| Read-only method | Use current state to return/print info | No (doesn't change attributes) |

### Read-Only Instance Methods
**Definition:** Methods that access object attributes using `self.attribute` to build return values or output, without changing any attributes.

**Pattern:**
```python
def method_name(self):
    """Description. Does NOT change any attributes (read-only)."""
    return f"{self.attribute1} {self.attribute2}"
```

### Using self in Methods
**Rule:** Inside a method, `self` refers to the specific object the method was called on. When `movie1.info()` runs, `self` is `movie1`.

---

## 3. Key Details to Remember

- **`__init__` sets starting state:** Constructor creates and initializes attributes
- **Read-only methods read state:** They use `self.attribute` but don't modify anything
- **self means "this object":** `self` refers to whichever object called the method
- **Docstrings:** Document read-only methods with `(read-only)` to clarify they don't modify state
- **File structure:** Use `# ---- class definitions ----` and `# ---- main program ----` sections

---

## 4. Examples

### Pet Class with describe() Method
```python
# ---- class definitions ----

class Pet:                                   # class representing a pet
    """Represents a pet with a name and species."""

    def __init__(self, name, species):        # constructor (sets starting state)
        """Set up the pet's starting state."""
        self.name = name                     # store name attribute
        self.species = species               # store species attribute

    def describe(self):                      # read-only instance method
        """Return a sentence about the pet. Does NOT change any attributes (read-only)."""
        return f"{self.name} is a {self.species}."

# ---- main program ----

pet1 = Pet("Milo", "cat")
print(pet1.describe())                        # Output: Milo is a cat.
```

### Book Class with summary() Method
```python
# ---- class definitions ----

class Book:                                  # class representing a book
    """Represents a book with a title and an author."""

    def __init__(self, title, author):        # constructor
        """Set up the book's starting state."""
        self.title = title                   # store title attribute
        self.author = author                  # store author attribute

    def summary(self):                       # read-only method
        """
        Return a short description of the book.
        Does NOT change any attributes (read-only).
        """
        return f'"{self.title}" is written by {self.author}.'

# ---- main program ----

book1 = Book("Dune", "Frank Herbert")
text = book1.summary()
print(text)                                  # Output: "Dune" is written by Frank Herbert.
```

### Movie Class with info() Method
```python
# ---- class definitions ----

class Movie:                                 # class representing a movie
    """Represents a movie with a title and year."""

    def __init__(self, title, year):          # constructor
        """Set up the movie's starting state."""
        self.title = title                   # store title attribute
        self.year = year                      # store year attribute

    def info(self):                          # read-only method
        """Return a formatted string about the movie."""
        return f"{self.title} ({self.year})"

# ---- main program ----

movie1 = Movie("The Matrix", 1999)
print(movie1.info())                         # Output: The Matrix (1999)
```

---

## 5. Common Mistakes / What Not to Do

| Mistake | Why It Fails |
|---------|--------------|
| Confusing `__init__` with read-only methods | `__init__` creates state; read-only methods use existing state |
| Modifying attributes in a read-only method | Violates the "read-only" contract |
| Forgetting `self` when accessing attributes | Must use `self.attribute`, not just `attribute` |
| Thinking `self` is the class | `self` is the specific object instance, not the class definition |

---

## 6. Open-Note Review

**Method Roles**
```python
# Constructor: creates and initializes attributes
def __init__(self, title, year):
    self.title = title
    self.year = year

# Read-only method: uses attributes, doesn't modify
def info(self):
    return f"{self.title} ({self.year})"  # reads only, no changes
```

**Key Distinction**
- `__init__` → Sets up starting state
- `describe()`/`info()`/`summary()` → Reads current state and returns something

**self Reference**
> Inside a method, `self` means "the specific object this method was called on."

---

## 7. Final Takeaway

The constructor (`__init__`) sets an object's starting state by creating and initializing attributes. Read-only instance methods then access those attributes via `self` to return or print information based on the current state, without modifying any attributes. Use docstrings to document which methods are read-only.

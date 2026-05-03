# Creating Multiple Objects from One Class

## 1. Lesson Focus
Shows how to create multiple independent objects from a single class, assign unique attributes to each using dot notation, and demonstrates that each object stores its own data separately.

---

## 2. Core Concepts

### Creating Objects from a Class
**Syntax:** `variable = ClassName()`

Each call creates a **new, separate object** — they share the blueprint but are independent instances.

```python
class Pet:
    pass

luna = Pet()  # First object
max = Pet()   # Second object (separate from luna)
```

### Dot Notation for Attributes
**Syntax:** `object.attribute = value`

Creates a new attribute inside that specific object. Other objects are unaffected.

```python
luna.name = "Luna"  # Only luna gets this attribute
max.name = "Max"    # Only max gets this attribute
```

### Independence of Objects
Each object keeps its own copy of attributes. Changing one object never affects another.

---

## 3. Key Details to Remember

- **Creating an object:** `luna = Pet()` makes a new object from the `Pet` blueprint
- **Creating attributes:** `luna.name = "Luna"` stores data inside that object
- **Multiple objects:** Can create many objects (`luna`, `max`, `buddy`, `rex`) from one class
- **Each object is independent:** `rex.trick_level = 10` does NOT change `buddy.trick_level`

---

## 4. Examples

### Basic Pet Example
```python
class Pet:
    pass

luna = Pet()
max = Pet()

luna.name = "Luna"
luna.age = 3

max.name = "Max"
max.age = 5

print(luna.name, luna.age, max.name, max.age)
# Output: Luna 3 Max 5
```

### Dog Example with Different Attributes
```python
class Dog:
    pass

buddy = Dog()
rex = Dog()

buddy.breed = "Beagle"
buddy.trick_level = 3

rex.breed = "German Shepherd"
rex.trick_level = 5

print(buddy.breed, buddy.trick_level, rex.breed, rex.trick_level)
# Output: Beagle 3 German Shepherd 5
```

### Changing One Object Doesn't Affect Others
```python
rex.trick_level = 10  # Only rex changes
# buddy.trick_level is still 3
```

---

## 5. Common Mistakes / What Not to Do

| Mistake | Why It Fails |
|---------|--------------|
| `class Pet: pass` does NOT create attributes | It only defines the blueprint |
| `luna = Pet` (no parentheses) | Assigns the class itself, not a new object |
| Expecting `rex.trick_level = 10` to change `buddy` | Objects are independent — each keeps its own data |

---

## 6. Open-Note Review

**Creating multiple objects**
```python
class Pet:
    pass

luna = Pet()  # Object 1
max = Pet()   # Object 2 (separate!)
```

**Assigning attributes**
```python
luna.name = "Luna"  # Dot notation: object.attribute = value
luna.age = 3
```

**Key rule**
> Each object stores its own data. Changing `rex.trick_level` never touches `buddy.trick_level`.

---

## 7. Final Takeaway

One class is a blueprint; calling `ClassName()` creates a new, independent object. Use dot notation (`object.attribute = value`) to give each object its own data. Each object maintains its own separate attributes — they do not share values, even when created from the same class.

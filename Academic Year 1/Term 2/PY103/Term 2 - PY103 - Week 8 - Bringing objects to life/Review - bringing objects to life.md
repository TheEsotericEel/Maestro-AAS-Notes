# Review: Bringing Objects to Life

## 1. Unit Focus
Covers the fundamentals of object-oriented programming in Python: defining classes, instantiating objects, using constructors, working with instance and class attributes, writing methods that use and change object state, and understanding identity vs equality.

---

## 2. Key Concepts Summary

### Class Definition and Instantiation
- **Class definition:** Creates the blueprint using `class ClassName:`
- **Instantiation:** Creates an object from the class using `ClassName()`
- Each object can store its own independent attribute values

### Attributes
- **Instance attributes:** Unique per object, set via `self.attribute` in `__init__` or after instantiation
- **Class attributes:** Shared by all instances, defined in class body outside methods
- **Adding attributes after instantiation:** Use `object.attribute = value`

### Methods
- **Method calling:** Use `object.method_name()`
- **`self` parameter:** Refers to the object the method was called on
- **Inside methods:** Use `self.attribute` to access object data
- **Outside class:** Use `object.attribute` to access object data

### Constructor (`__init__`)
- **Runs automatically:** During instantiation when `ClassName()` is called
- **Purpose:** Set up initial object state and attributes
- **Validation:** Can check and correct invalid inputs without exceptions

### Identity vs Equality
- **`is` operator:** Checks if two names point to the same object in memory
- **`==` operator:** For custom classes, defaults to identity check unless overridden
- **Aliasing:** `t3 = t1` means both names reference the same object

---

## 3. Important Patterns

### Minimal Class
```python
class Dog:
    pass
```

### Constructor with Parameters
```python
class ClassName:
    def __init__(self, param):
        self.attribute = param
```

### Method Definition and Call
```python
class ClassName:
    def method_name(self):
        self.attribute = value

obj = ClassName()
obj.method_name()
```

### Validation in Constructor (Without Exceptions)
```python
def __init__(self, age):
    if age < 0:
        age = 0
    self.age = age
```

### Instance Attribute After Instantiation
```python
s = Student()
s.name = "Dana"
```

### Class Attribute Pattern
```python
class Team:
    members = 0  # shared by all instances

    def __init__(self, name):
        self.name = name
        Team.members += 1
```

---

## 4. Quick Reference

| Concept | Syntax |
|---------|--------|
| Class definition | `class ClassName:` |
| Instantiation | `obj = ClassName()` |
| Instance attribute | `self.attr` (inside), `obj.attr` (outside) |
| Class attribute | Defined in class body, shared |
| Method call | `obj.method()` |
| Constructor | `def __init__(self, params):` |
| Identity check | `obj1 is obj2` |
| Equality check | `obj1 == obj2` |

---

## 5. Final Takeaway

Classes define blueprints for objects; instantiation creates specific objects with independent state. Instance attributes store per-object data via `self`, while class attributes store shared data. Methods use `self` to access and modify object state. The constructor `__init__` runs automatically during instantiation to set initial state. Use `is` for identity checks and `==` for equality (defaults to identity for custom classes).



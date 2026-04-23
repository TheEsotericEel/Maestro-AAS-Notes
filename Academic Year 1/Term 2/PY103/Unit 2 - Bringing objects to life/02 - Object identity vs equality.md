# Object Identity vs Equality

## 1. Lesson Focus
Explains the difference between **identity** (whether two variables point to the same object) and **equality** (whether objects have the same value), and why this distinction matters for debugging mutation bugs.

---

## 2. Core Concepts

### Identity (`is`)
**Question:** "Do these two variables point to the same exact object in memory?"

**Syntax:** `a is b` → `True` if both variables refer to the same object

```python
a = [1, 2]
b = a        # Same object
a is b       # True
```

### Equality (`==`)
**Question:** "Do these objects have the same value or contents?"

**Syntax:** `a == b` → `True` if contents/values match

```python
a = [1, 2]
c = [1, 2]   # Different object, same contents
a == c       # True
a is c       # False
```

### Behavior by Type

| Type | `==` compares | `is` always |
|------|---------------|-------------|
| **Built-ins** (lists, dicts, strings) | Contents/values | Identity |
| **Simple custom classes** (like `Pet`) | Defaults to identity | Identity |

For built-in types: `a == b` can be `True` while `a is b` is `False`.
For simple custom classes without customization: `==` behaves like `is`.

---

## 3. Key Details to Remember

- **`is`** → identity: same object in memory (one shared T-shirt)
- **`==`** → equality: same value/contents (two identical T-shirts)
- **Aliasing:** `b = a` creates two names for the same object — mutations through one affect the other
- **Copying:** `b = a.copy()` creates a new object with the same contents — independent
- **When debugging:** ask "Do these refer to the same object?" not just "Do they look the same?"

---

## 4. Examples

### List Identity vs Equality
```python
a = [1, 2]
b = a          # Alias: same object
c = [1, 2]     # Copy: different object, same contents

print(a is b)  # True  (same object)
print(a is c)  # False (different objects)
print(a == c)  # True  (same contents)
```

### Aliasing and Mutation
```python
a = [1, 2]
b = a          # Alias
a.append(3)

print(a)  # [1, 2, 3]
print(b)  # [1, 2, 3]  ← Changed too (same object)
```

### Copying and Independence
```python
a = [1, 2]
b = a.copy()  # New object
a.append(3)

print(a)  # [1, 2, 3]
print(b)  # [1, 2]     ← Unchanged (different object)
```

### Custom Objects (Simple Pet Class)
```python
class Pet:
    pass

pet1 = Pet()
pet2 = pet1           # Alias
pet1.name = "Luna"

print(pet1.name)      # Luna
print(pet2.name)      # Luna  ← Same object
```

### Two Separate Objects with Same Value
```python
class Pet:
    pass

pet1 = Pet()
pet2 = Pet()          # Different objects
pet1.name = "Luna"
pet2.name = "Luna"

print(pet1 is pet2)   # False (different objects)
print(pet1 == pet2)   # False  (== acts like is for simple classes)
```

### Identity in Lists (Buggy Pattern)
```python
class Pet:
    pass

pet1 = Pet()
pet2 = pet1           # ⚠ Alias, not a new pet

pets = []
pets.append(pet1)
pets.append(pet2)

print(len(pets))          # 2
print(pets[0] is pets[1]) # True  ← Same object twice!
```

### Fix: Create Separate Objects
```python
pet1 = Pet()
pet1.name = "Luna"

pet2 = Pet()             # ✅ New object
pet2.name = "Luna"

pets.append(pet1)
pets.append(pet2)

print(len(pets))          # 2
print(pets[0] is pets[1]) # False  ← Different objects
```

---

## 5. Common Mistakes / What Not to Do

| Mistake | Why It Fails |
|---------|--------------|
| Expecting `pet1 == pet2` to be `True` for simple custom classes | `==` defaults to identity unless you customize `__eq__` |
| Thinking `b = a` creates a copy | It creates an alias — same object |
| Ignoring identity when debugging mutations | Mystery mutations happen because of shared objects |
| Using `==` to check if lists share mutations | Use `is` to check identity |

---

## 6. Open-Note Review

**Quick Reference**

| Operator | Question | When True |
|----------|----------|-----------|
| `is` | Same object? | Variables point to identical object in memory |
| `==` | Same value? | Contents match (for built-ins) |

**Aliasing vs Copying**
```python
b = a        # Alias → same object
b = a.copy() # Copy → new object, same contents
```

**Debugging Question**
> "Do these variables refer to the same object?" — not just "Do they look the same?"

---

## 7. Final Takeaway

**Identity (`is`)** asks if two variables point to the same object in memory. **Equality (`==`)** asks if objects have the same value. For built-ins, `==` compares contents; for simple custom classes, `==` defaults to identity. Aliasing (`b = a`) shares identity, so mutations spread — this is the source of "mystery mutation" bugs. When debugging, ask "Do these refer to the same object?"

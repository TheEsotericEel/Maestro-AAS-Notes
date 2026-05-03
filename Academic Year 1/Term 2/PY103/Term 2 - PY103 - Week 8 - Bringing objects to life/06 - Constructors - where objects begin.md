# Constructors: Where Objects Begin

## 1. Lesson Focus
Introduces the `__init__` constructor method — a special method that runs automatically when creating a new object, allowing you to set default attribute values without repeating setup code for every instance.

---

## 2. Core Concepts

### Constructor (`__init__`)
**Definition:** A special method in Python classes that runs automatically right after creating a new object.

**Purpose:** Set up initial state (default attribute values) for each new object.

**Syntax:**
```python
class ClassName:
    def __init__(self):
        self.attribute = default_value
```

### When `__init__` Runs
- **Automatically** — immediately after `ClassName()` is called
- **Not manually** — you never call `object.__init__()` yourself
- **Per object** — runs once for each new object created

### The Problem Without Constructors
Without `__init__`, you repeat setup code for every object:
```python
pet1 = Pet()
pet1.name = "Fluffy"
pet1.happiness = 50

pet2 = Pet()
pet2.name = "Spot"
pet2.happiness = 50
```

With `__init__`, setup happens automatically.

---

## 3. Key Details to Remember

- **`__init__` syntax:** Always `def __init__(self):` with double underscores
- **Automatic execution:** Python calls `__init__` right after `ClassName()`
- **Default values:** Use `self.attribute = value` inside `__init__` to set initial state
- **Runs per object:** Each `ClassName()` call triggers `__init__` once for that object
- **Don't call manually:** Never write `object.__init__()` — Python handles it

---

## 4. Examples

### Pet Class with Constructor
```python
class Pet:
    def __init__(self):
        self.name = "Unnamed"
        self.happiness = 50

pet1 = Pet()
print(pet1.name)       # Unnamed
print(pet1.happiness)  # 50

pet2 = Pet()
print(pet2.name)       # Unnamed
print(pet2.happiness)  # 50
```

### Lamp Class with Constructor
```python
class Lamp:
    def __init__(self):
        self.is_on = False
        self.brightness = 0

lamp1 = Lamp()
print(lamp1.is_on)      # False
print(lamp1.brightness) # 0
```

### Object Creation Timeline
When `pet = Pet()` runs:
1. Python creates space in memory for the new Pet object
2. Python automatically calls `pet.__init__()` for you
3. `__init__` sets `self.name = "Unnamed"` and `self.happiness = 50`
4. Object is ready to use

---

## 5. Common Mistakes / What Not to Do

| Mistake | Why It Fails |
|---------|--------------|
| Calling `__init__` manually | `pet.__init__()` is unnecessary — Python calls it automatically |
| Forgetting `self` parameter | `def __init__():` without `self` will cause errors |
| Not using double underscores | `def init(self):` won't be recognized as a constructor |
| Setting attributes after creation | Defeats the purpose of `__init__` — use it to set defaults |

---

## 6. Open-Note Review

**Constructor Pattern**
```python
class ClassName:
    def __init__(self):
        self.attribute = default_value
```

**Triggering Constructor**
```python
object = ClassName()  # This automatically calls __init__
```

**Key Rule**
> `__init__` runs automatically right after `ClassName()` — you don't call it yourself.

---

## 7. Final Takeaway

The `__init__` constructor is a special method that runs automatically when creating a new object. Use it to set default attribute values on `self`, avoiding repetitive setup code. When you write `ClassName()`, Python creates the object and immediately calls `__init__` for you — never call `__init__` manually.

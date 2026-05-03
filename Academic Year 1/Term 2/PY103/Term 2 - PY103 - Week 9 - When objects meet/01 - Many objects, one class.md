# Many Objects, One Class

## 1. Lesson Focus
Demonstrates that multiple objects created from the same class share the same blueprint but have independent states — changing one object does not affect others.

---

## 2. Core Concepts

### Multiple Objects from One Class
**Definition:** Creating multiple instances from a single class definition. Each object starts with the same attributes and initial values but maintains its own separate state in memory.

**Key Idea:** Same blueprint, separate lives in memory.

### Independent State
**Definition:** Each object maintains its own copy of instance attributes. Changes to one object's attributes do not affect other objects created from the same class.

**Contrast:**
- **Class attributes:** Shared by all instances
- **Instance attributes:** Unique per object

---

## 3. Key Details to Remember

- **Same foundation:** All objects from a class start with the same attributes and initial values (set by `__init__`)
- **Independent state:** Each object has its own copy of instance attributes in memory
- **Isolated changes:** Calling a method on one object only affects that object's state
- **No shared instance data:** Objects don't share instance attribute values unless explicitly designed to

---

## 4. Examples

### Stopwatch Class
```python
class Stopwatch:                            # class blueprint
    def __init__(self):                     # constructor
        self.elapsed = 0                    # every stopwatch starts at 0

    def tick(self):                         # mutator method
        self.elapsed += 5                   # add 5 seconds
```

### Creating Multiple Stopwatches
```python
sw1 = Stopwatch()                          # first object
sw2 = Stopwatch()                          # second object

print("sw1 start:", sw1.elapsed)           # Output: 0
print("sw2 start:", sw2.elapsed)           # Output: 0
# Both start with same state
```

### Changing One Object
```python
sw1.tick()                                 # only change sw1

print("sw1 after tick:", sw1.elapsed)      # Output: 5
print("sw2 after tick:", sw2.elapsed)      # Output: 0
# Only sw1 changed, sw2 unchanged
```

### Independent State Accumulation
```python
sw2.tick()
sw2.tick()

print("sw1 final:", sw1.elapsed)           # Output: 5 (1 tick)
print("sw2 final:", sw2.elapsed)           # Output: 10 (2 ticks)
# Each object tracks its own elapsed time independently
```

---

## 5. Common Mistakes / What Not to Do

| Mistake | Why It Fails |
|---------|--------------|
| Assuming changing one object affects all | Instance attributes are not shared between objects |
| Adding unnecessary parameters to `__init__` | If all objects start the same, don't add parameters |
| Using `=` instead of `+=` for accumulation | `=` sets the value, `+=` adds to existing value |

---

## 6. Open-Note Review

**Class Blueprint Pattern**
```python
class ClassName:
    def __init__(self):
        self.attribute = initial_value    # same start for all

    def method(self):
        self.attribute += delta          # changes only this object
```

**Multiple Objects Pattern**
```python
obj1 = ClassName()
obj2 = ClassName()
obj1.method()  # only obj1 changes
```

**Key Rule**
> Objects from the same class start with the same foundation but can be manipulated independently. Each object maintains its own state in memory.

---

## 7. Final Takeaway

Multiple objects created from the same class share the same blueprint and initial state, but each object maintains its own independent state in memory. Changing one object through its methods does not affect other objects created from the same class.

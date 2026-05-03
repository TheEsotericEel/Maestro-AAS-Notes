# Reading Object State

## 1. Lesson Focus
Teaches how to read an object's current state using dot notation, compare states of multiple objects, and track which attributes change or stay the same over time.

---

## 2. Core Concepts

### Object State
**Definition:** The set of all attribute values an object holds at a given moment. Think of it as a frozen snapshot in time.

**Reading State:** Use dot notation `obj.attribute` to read the current value stored in an attribute.

```python
obj.attribute  # reads/looks at the value, does not change it
```

### State Snapshot
**Definition:** A mental picture of all attribute values at a specific point in code execution.

**Example:**
```python
# After p = Player("Alex", 10)
p.name → "Alex"
p.score → 10
```

### Comparing States
**Skill:** Reading code and determining:
- What each object's state is at different points
- Which attributes changed between snapshots
- Which attributes stayed the same

---

## 3. Key Details to Remember

- **Dot notation reads state:** `obj.attribute` retrieves the current value without changing it
- **Each object has independent state:** Changes to one object don't affect others
- **Track changes:** Compare before/after snapshots to see what changed
- **Identify unchanged attributes:** Some attributes may stay the same throughout

---

## 4. Examples

### Player State
```python
class Player:                              # class representing a player
    def __init__(self, name, score):       # constructor
        self.name = name                   # instance attribute
        self.score = score                 # instance attribute

p = Player("Alex", 10)
print(p.score)                            # Output: 10
```

**State snapshot of p:**
- `name` → "Alex"
- `score` → 10

### BankAccount State Comparison
```python
class BankAccount:                         # class representing a bank account
    def __init__(self, owner, balance):    # constructor
        self.owner = owner                 # instance attribute
        self.balance = balance             # instance attribute

a1 = BankAccount("Sam", 100)
a2 = BankAccount("Jordan", 250)

a1.balance = a1.balance + 50             # deposit into a1
```

**Before deposit:**
- a1: owner = "Sam", balance = 100
- a2: owner = "Jordan", balance = 250

**After deposit:**
- a1: owner = "Sam", balance = 150 (changed)
- a2: owner = "Jordan", balance = 250 (unchanged)

### Timer State Tracking
```python
class Timer:                               # class representing a timer
    def __init__(self, label, seconds):   # constructor
        self.label = label                 # instance attribute
        self.seconds = seconds             # instance attribute

t1 = Timer("Workout", 0)
t2 = Timer("Rest", 0)

t1.seconds = t1.seconds + 30
t2.seconds = t2.seconds + 10
t1.seconds = t1.seconds + 5
```

**Final state:**
- t1: label = "Workout", seconds = 35 (0 + 30 + 5)
- t2: label = "Rest", seconds = 10 (0 + 10)

**Explanation:** t1 had more time added (35 total vs 10 total).

### Lamp State Change
```python
class Lamp:                                # class representing a lamp
    def __init__(self, color, brightness): # constructor
        self.color = color                 # instance attribute
        self.brightness = brightness       # instance attribute

lamp1 = Lamp("blue", 3)
lamp2 = Lamp("red", 5)

lamp1.brightness = 4
```

**Final state:**
- lamp1: color = "blue", brightness = 4 (changed)
- lamp2: color = "red", brightness = 5 (unchanged)

### Car Mileage State
```python
class Car:                                 # class representing a car
    def __init__(self, model, mileage):    # constructor
        self.model = model                 # instance attribute
        self.mileage = mileage             # instance attribute

c1 = Car("Sedan", 10000)
c2 = Car("SUV", 5000)

c1.mileage = c1.mileage + 500
```

**Final state:**
- c1.mileage = 10500 (changed)
- c2.mileage = 5000 (unchanged)

### Phone Battery State
```python
class Phone:                               # class representing a phone
    def __init__(self, owner, battery):    # constructor
        self.owner = owner                 # instance attribute
        self.battery = battery             # instance attribute (percent)

p1 = Phone("Alex", 80)
p2 = Phone("Riley", 50)

p1.battery = p1.battery - 30
p2.battery = p2.battery + 20
```

**Final state:**
- p1: owner = "Alex", battery = 50 (changed)
- p2: owner = "Riley", battery = 70 (changed)

**Changed:** p1.battery, p2.battery
**Unchanged:** p1.owner, p2.owner

### Download State Snapshots
```python
class Download:                            # class representing a download
    def __init__(self, file_name, percent): # constructor
        self.file_name = file_name         # instance attribute
        self.percent = percent             # instance attribute

d = Download("movie.mp4", 0)              # Snapshot A
d.percent = 20                            # Snapshot B
d.percent = 75                            # Snapshot C
```

**Snapshots:**
- A: file_name = "movie.mp4", percent = 0
- B: file_name = "movie.mp4", percent = 20
- C: file_name = "movie.mp4", percent = 75

**Unchanged across all snapshots:** file_name

---

## 5. Common Mistakes / What Not to Do

| Mistake | Why It Fails |
|---------|--------------|
| Thinking `obj.attr` changes the value | Dot notation reads, doesn't modify |
| Assuming changes to one object affect others | Each object has independent state |
| Forgetting to track unchanged attributes | Some attributes may stay the same throughout |
| Confusing which object was modified | Carefully track which `obj.` prefix is used |

---

## 6. Open-Note Review

**Reading State Pattern**
```python
obj.attribute  # reads current value
```

**State Snapshot Format**
```
obj: attr1 = value1, attr2 = value2
```

**Change Tracking**
- Compare before/after snapshots
- Identify which attributes changed
- Identify which attributes stayed the same

**Key Rule**
> Use dot notation to read object state. Compare snapshots to track changes. Each object maintains independent state.

---

## 7. Final Takeaway

Reading object state means using dot notation (`obj.attribute`) to retrieve current attribute values. Think of state as a snapshot at a moment in time. Compare snapshots before and after code runs to identify which attributes changed and which stayed the same. Each object has independent state — changes to one don't affect others.

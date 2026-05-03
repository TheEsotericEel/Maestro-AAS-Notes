# Challenge II

## 1. Lesson Focus
A challenge lesson practicing object-oriented programming concepts: using `self` in methods to change object state, protecting invariants (values staying within valid ranges), and understanding identity vs equality with custom classes.

---

## 2. Core Concepts

### Using self in Methods
**Rule:** Inside methods, use `self.attribute` to work with the specific object's data. Outside the class, use `object.attribute`.

**Where to use self:**
- In `__init__` to store data on the object: `self.attribute = value`
- In other methods to read or change data: `self.attribute += delta`

### Protecting Invariants
**Definition:** Ensuring object attributes stay within valid bounds (e.g., never going below 0).

**Pattern:**
```python
def method(self, amount):
    self.attribute -= amount
    if self.attribute < minimum:
        self.attribute = minimum
```

### Identity vs Equality
| Operator | Checks | Example Result |
|----------|--------|----------------|
| `is` | Same object in memory? | `t1 is t3` → True if aliases |
| `==` | Same data? (custom classes default to identity) | `t1 == t2` → False for different objects |

**Key Rule:** For simple custom classes without special methods, `==` behaves like `is` — it checks identity, not data equality.

---

## 3. Key Details to Remember

- **Inside methods:** Use `self.attribute` and `self.method(...)`
- **Outside class:** Use `object.attribute` and `object.method(...)`
- **State change:** Methods can modify `self.attribute` values
- **Invariants:** Use `if` checks to keep values within valid ranges
- **Identity:** `is` checks if two names point to the same object
- **Equality:** For custom classes, `==` defaults to identity unless overridden

---

## 4. Examples

### BankAccount with deposit()
```python
class BankAccount:                          # class representing a bank account
    def __init__(self, owner, balance):    # constructor
        self.owner = owner                 # instance attribute
        self.balance = balance              # instance attribute

    def deposit(self, amount):             # mutator method
        self.balance = self.balance + amount

acc = BankAccount("Alex", 100)
acc.deposit(50)
print(acc.balance)                        # Output: 150
```

### Light with switch_on()
```python
class Light:                               # class representing a light
    def __init__(self):                    # constructor
        self.on = False                    # light starts off

    def switch_on(self):                   # mutator method
        self.on = True                     # turn THIS light on

lamp = Light()
lamp.switch_on()
print(lamp.on)                            # Output: True
```

### Counter with increment()
```python
class Counter:                             # class representing a counter
    def __init__(self):                    # constructor
        self.value = 0                     # starts at 0

    def increment(self):                   # mutator method
        self.value += 1                    # increase by 1

c = Counter()
c.increment()
print(c.value)                            # Output: 1
```

### Battery with drain() (Protects Invariant)
```python
class Battery:                             # class representing a battery
    def __init__(self, level):             # constructor
        self.level = level                 # battery level (0-100)

    def drain(self, amount):               # mutator method
        self.level -= amount               # reduce level
        if self.level < 0:                 # protect invariant
            self.level = 0                 # don't go below 0

b = Battery(10)
b.drain(7)
print(b.level)                            # Output: 3

b.drain(10)
print(b.level)                            # Output: 0 (not -7)
```

### WaterBottle with drink() (Protects Invariant)
```python
class WaterBottle:                         # class representing a water bottle
    def __init__(self, capacity):         # constructor
        self.capacity = capacity           # total capacity
        self.current = capacity            # starts full

    def drink(self, amount):              # mutator method
        self.current -= amount            # reduce water
        if self.current < 0:              # protect invariant
            self.current = 0               # don't go below 0

bottle = WaterBottle(100)
bottle.drink(30)
print(bottle.current)                     # Output: 70

bottle.drink(100)
print(bottle.current)                     # Output: 0 (not -30)
```

### Identity vs Equality
```python
class Ticket:                              # class representing a ticket
    def __init__(self, seat):              # constructor
        self.seat = seat

t1 = Ticket("A10")                         # first Ticket object
t2 = Ticket("A10")                         # second Ticket object (different)
t3 = t1                                    # t3 is an alias to t1

print(t1 is t2)                            # Output: False (different objects)
print(t1 is t3)                            # Output: True (same object)
print(t1 == t2)                            # Output: False (identity check)
```

---

## 5. Common Mistakes / What Not to Do

| Mistake | Why It Fails |
|---------|--------------|
| Using object name inside method | `lamp.on = True` only works if the object is named `lamp` — use `self.on` instead |
| Forgetting `self` when assigning | `on = True` creates a local variable, not an attribute |
| Not protecting invariants | Values can go outside valid ranges (e.g., negative balances) |
| Confusing `is` with `==` | `is` checks identity, `==` checks equality (but defaults to identity for custom classes) |

---

## 6. Open-Note Review

**self Usage Rule**
> Inside methods: `self.attribute`. Outside class: `object.attribute`.

**Invariant Protection Pattern**
```python
def method(self, amount):
    self.attribute -= amount
    if self.attribute < minimum:
        self.attribute = minimum
```

**Identity vs Equality**
```python
t1 is t2    # True only if same object in memory
t1 == t2    # For custom classes, behaves like is unless overridden
t3 = t1     # t3 and t1 are aliases (same object)
```

---

## 7. Final Takeaway

Use `self` inside methods to access and modify object attributes. Protect invariants with conditional checks to keep values within valid ranges. Remember that `is` checks object identity, while `==` defaults to identity for custom classes unless special methods are defined.

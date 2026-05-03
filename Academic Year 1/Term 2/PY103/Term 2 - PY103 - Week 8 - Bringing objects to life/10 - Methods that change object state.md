# Methods That Change Object State

## 1. Lesson Focus
Shows how to write **mutator methods** that modify an object's attributes via `self`, causing the object's state to change and persist across multiple method calls.

---

## 2. Core Concepts

### Mutator Methods
**Definition:** Methods that modify an object's attributes by assigning new values to `self.attribute`.

**Pattern:**
```python
def method_name(self):
    self.attribute = new_value  # or self.attribute += delta
```

### State Persistence
**Key Idea:** When a method changes `self.attribute`, the new value is stored on the object and persists for subsequent method calls. The object "remembers" its state.

### Read-Only vs Mutator Methods
| Method Type | Uses `self.attribute` | Modifies Attributes? |
|-------------|---------------------|---------------------|
| Read-only | To read and return/print | No |
| Mutator | To update | Yes |

---

## 3. Key Details to Remember

- **Mutator methods change state:** They assign new values to `self.attribute`
- **Changes persist:** Modified attribute values stay on the object between method calls
- **Compound assignment:** Common patterns like `self.hunger -= 2` or `self.level += 10`
- **Each call builds on current state:** The object remembers previous changes

---

## 4. Examples

### Pet Class with feed() Method
```python
class Pet:                                   # class representing a pet
    def __init__(self, name):                # constructor
        self.name = name
        self.hunger = 5                      # initial hunger level
        self.happiness = 3                    # initial happiness level

    def feed(self):                          # mutator method
        print("Feeding", self.name)
        self.hunger -= 2                     # decrease hunger
        self.happiness += 1                   # increase happiness

pet = Pet("Luna")

print("Before feeding:")
print("hunger:", pet.hunger)                 # Output: 5
print("happiness:", pet.happiness)           # Output: 3

pet.feed()

print("After 1st feed:")
print("hunger:", pet.hunger)                 # Output: 3 (5 - 2)
print("happiness:", pet.happiness)           # Output: 4 (3 + 1)

pet.feed()

print("After 2nd feed:")
print("hunger:", pet.hunger)                 # Output: 1 (3 - 2)
print("happiness:", pet.happiness)           # Output: 5 (4 + 1)
```

### Battery Class with charge() Method
```python
class Battery:                               # class representing a battery
    def __init__(self):                      # constructor
        self.level = 0                       # initial charge level

    def charge(self):                        # mutator method
        self.level += 10                     # increase charge by 10

battery = Battery()

print("Initial level:", battery.level)        # Output: 0

battery.charge()
print("After 1st charge:", battery.level)    # Output: 10

battery.charge()
print("After 2nd charge:", battery.level)    # Output: 20

battery.charge()
print("After 3rd charge:", battery.level)    # Output: 30
```

### State Change Tracking
```python
# Starting state: hunger = 5, happiness = 3
pet.feed()  # hunger: 3, happiness: 4
pet.feed()  # hunger: 1, happiness: 5
# Each call modifies the current state
```

---

## 5. Common Mistakes / What Not to Do

| Mistake | Why It Fails |
|---------|--------------|
| Forgetting `self` when assigning | `hunger -= 2` creates a local variable, not an attribute |
| Not understanding persistence | Changes don't "reset" between calls — they accumulate |
| Confusing read-only with mutator | Read-only methods don't modify; mutators do |
| Expecting methods to return modified values | Mutators change `self` directly, don't need to return |

---

## 6. Open-Note Review

**Mutator Pattern**
```python
def method_name(self):
    self.attribute = new_value       # direct assignment
    self.attribute += delta          # compound assignment
```

**State Persistence Example**
```python
# level starts at 0
charge()  # level becomes 10
charge()  # level becomes 20 (builds on previous state)
charge()  # level becomes 30
```

**Key Rule**
> When a method modifies `self.attribute`, the change persists on the object for subsequent calls.

---

## 7. Final Takeaway

Mutator methods modify an object's attributes by assigning new values to `self.attribute`. These state changes persist across method calls — the object "remembers" its modified values. Each subsequent method call operates on the current state, building on previous changes.

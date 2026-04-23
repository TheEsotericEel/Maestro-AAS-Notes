# Classes and Instances

## 1. Lesson Focus
Introduces **classes** (blueprints) and **instances** (objects made from those blueprints), and covers Python naming conventions for each.

---

## 2. Core Concepts

### Class
**Definition:** A blueprint that defines the shared structure and behavior for a type of object.

- Describes what all objects of that type *will have* (state) and *can do* (behavior)
- Does not represent one specific thing — it's the template

### Instance
**Definition:** A specific object created from a class.

- One concrete thing built using the class blueprint
- Each instance can have its own data values, but shares the same structure

### The Relationship
```
Class (blueprint)  →  creates many →  Instances (objects)

Pet                →               →  luna, max, nibbles
```

One class → unlimited instances, each independent.

---

## 3. Python Naming Conventions

| Thing | Style | Example |
|-------|-------|---------|
| **Class** | CapitalCase (PascalCase) | `Pet`, `MagicCar`, `BankAccount` |
| **Instance / variable** | snake_case | `my_pet`, `red_car`, `luna` |

**Quick rule:** If you see a name starting with a capital letter in Python, it's almost certainly a class.

---

## 4. Examples

### Pet game example
```
Class:     Pet          ← the blueprint (describes all pets)
Instances: luna         ← a 3-year-old cat
           max          ← a 5-year-old dog
           nibbles      ← a 1-year-old hamster
```
All three instances come from the same `Pet` blueprint.

### Identifying class vs. instance by name
| Name | Class or Instance? | Why |
|------|--------------------|-----|
| `Pet` | Class | CapitalCase |
| `my_pet` | Instance | snake_case |
| `MagicCar` | Class | CapitalCase |
| `red_car` | Instance | snake_case |

---

## 5. Open-Note Review

- **Class** = blueprint; defines structure/behavior for a type of object
- **Instance** = a specific object made from that blueprint
- One class → many instances
- Classes → `CapitalCase`; instances → `snake_case`

**Quick self-test**
> If `Car` is a class, what would you call one specific red sports car? → `my_car` or `red_car` (an instance)

---

## 6. Final Takeaway

A **class** is the blueprint; an **instance** is one specific object built from it. `Pet` defines what all pets are like — `luna` and `max` are individual pets made from that blueprint. In Python, spot the difference by naming style: `CapitalCase` = class, `snake_case` = instance.

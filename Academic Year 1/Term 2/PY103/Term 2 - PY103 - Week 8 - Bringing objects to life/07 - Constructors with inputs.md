# Constructors with Inputs

## 1. Lesson Focus
Shows how to write constructors that accept parameters, allowing objects to be initialized with specific data when created, and explains the difference between parameters (method inputs) and attributes (stored values on objects).

---

## 2. Core Concepts

### Constructor Parameters
**Definition:** Values passed into `__init__` when creating an object, used to initialize the object's attributes.

**Syntax:**
```python
class ClassName:                              # class (blueprint)
    def __init__(self, param1, param2):       # parameters (inputs)
        self.param1 = param1                  # attributes (stored on object)
        self.param2 = param2
```

### Parameters vs Attributes

| Term | What It Is | Example |
|------|------------|---------|
| **Parameter** | Input to the method | `event`, `seat` in `def __init__(self, event, seat)` |
| **Attribute** | Value stored on the object | `self.event`, `self.seat` |

### Passing Arguments to Constructors
When creating an object, pass arguments that match the constructor's parameters:

```python
object = ClassName(arg1, arg2)  # Arguments passed to __init__
```

---

## 3. Key Details to Remember

- **Parameters** are inputs to the `__init__` method
- **Attributes** are values stored on the object (`self.attribute`)
- **Required parameters** must be provided when creating the object
- **Missing arguments** cause `TypeError: missing required positional arguments`
- **Pattern:** `self.attribute = parameter` — store parameter as attribute

---

## 4. Examples

### Ticket Class with Constructor Parameters
```python
class Ticket:                                # class (blueprint for ticket objects)
    def __init__(self, event, seat):         # constructor method, runs when Ticket is created
        self.event = event                   # store event parameter as attribute on this Ticket
        self.seat = seat                     # store seat parameter as attribute on this Ticket

my_ticket = Ticket("Rock Festival", "A12")   # pass event + seat into constructor
print(my_ticket.event)                       # Output: Rock Festival
print(my_ticket.seat)                        # Output: A12
```

### Missing Required Arguments (Error)
```python
broken_ticket = Ticket()                     # ❌ missing event and seat arguments
# TypeError: Ticket.__init__() missing 2 required positional arguments: 'event' and 'seat'
```

### Partial Arguments (Error)
```python
partial_ticket = Ticket("Concert")            # ❌ missing seat argument
# TypeError: Ticket.__init__() missing 1 required positional argument: 'seat'
```

### Correct Argument Passing
```python
ticket = Ticket("Concert", "A5")             # ✅ both arguments provided
```

---

## 5. Common Mistakes / What Not to Do

| Mistake | Why It Fails |
|---------|--------------|
| `Ticket()` with no arguments | Constructor requires `event` and `seat` parameters |
| `Ticket("Game")` with one argument | Missing the `seat` parameter |
| Confusing parameters with attributes | Parameters are inputs; attributes are stored values |
| Forgetting `self.` when assigning | `event = event` creates a local variable, not an attribute |

---

## 6. Open-Note Review

**Constructor Pattern with Parameters**
```python
class ClassName:                              # class
    def __init__(self, param1, param2):       # parameters (inputs)
        self.param1 = param1                  # attributes (stored)
        self.param2 = param2

object = ClassName(arg1, arg2)               # pass arguments
```

**Key Distinction**
- `event`, `seat` → parameters (inputs to `__init__`)
- `self.event`, `self.seat` → attributes (stored on object)

**Rule**
> If the constructor expects parameters, you must pass all of them when creating the object.

---

## 7. Final Takeaway

Constructors can accept parameters to initialize objects with specific data. Parameters are inputs to `__init__`; attributes are values stored on the object via `self.attribute = parameter`. All required parameters must be provided when creating an object, or Python raises a `TypeError`.

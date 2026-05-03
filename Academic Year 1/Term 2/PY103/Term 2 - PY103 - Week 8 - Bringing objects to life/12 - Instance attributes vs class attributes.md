# Instance Attributes vs Class Attributes

## 1. Lesson Focus
Distinguishes between **instance attributes** (unique per object) and **class attributes** (shared by all instances), and provides a rule of thumb for choosing where to store data in a class design.

---

## 2. Core Concepts

### Instance Attribute
**Definition:** Data stored on each individual object, unique to that instance. Defined inside `__init__` with `self.attribute`.

**Syntax:**
```python
def __init__(self, value):
    self.attribute = value  # instance attribute
```

### Class Attribute
**Definition:** Data stored on the class itself, shared by all instances. Defined in the class body, outside any method.

**Syntax:**
```python
class ClassName:
    CLASS_ATTR = value  # class attribute (shared)
```

### Attribute Shadowing
**Definition:** When an instance attribute has the same name as a class attribute, the instance attribute "shadows" or hides the class attribute for that specific object.

**Example:**
```python
class Pet:
    species = "dog"      # class attribute

fido = Pet()
fido.species = "wolf"    # creates instance attribute, shadows class attribute for fido
```

### Decision Rule of Thumb
| Value Characteristic | Store On |
|----------------------|-----------|
| Usually the same for all objects | Class attribute |
| Different for each object | Instance attribute |

---

## 3. Key Details to Remember

- **Instance attributes:** Unique per object, defined with `self.attribute` in `__init__`
- **Class attributes:** Shared by all instances, defined in class body outside methods
- **Shadowing:** An instance attribute with the same name hides the class attribute for that object
- **Access patterns:** Both `ClassName.attr` and `instance.attr` work for class attributes
- **Shared state:** Changing a class attribute updates the value for all instances

---

## 4. Examples

### Pet Class: Instance vs Class Attributes
```python
class Pet:                                   # class representing a pet
    species = "dog"                          # class attribute (shared)

    def __init__(self, name):                 # constructor
        self.name = name                     # instance attribute (unique per pet)

fido = Pet("Fido")
luna = Pet("Luna")

print(fido.species)                          # Output: dog (from class)
print(luna.species)                          # Output: dog (from class)

Pet.species = "cat"                           # change class attribute

print(fido.species)                          # Output: cat (shared value updated)
print(luna.species)                          # Output: cat
```

### Shadowing Example
```python
class Pet:
    species = "dog"

fido = Pet("Fido")
luna = Pet("Luna")

Pet.species = "cat"
fido.species = "wolf"                         # creates instance attribute on fido

print(Pet.species)                          # Output: cat (class value)
print(fido.species)                          # Output: wolf (instance shadows class)
print(luna.species)                          # Output: cat (still uses class value)
```

### Pet with Shared Counter
```python
class Pet:
    default_sound = "awoo"                    # class attribute (shared)
    global_population = 0                     # class attribute (shared counter)

    def __init__(self, name):                # constructor
        self.name = name                     # instance attribute
        Pet.global_population += 1           # increment shared counter

pet1 = Pet("Dug")
pet2 = Pet("Bill")
pet3 = Pet("Henry")

print(Pet.global_population)                 # Output: 3
```

### GameSettings Example
```python
class GameSettings:                          # class for game configuration
    screen_width = 1920                      # class attribute (shared)
    screen_height = 1080                     # class attribute (shared)

    def __init__(self, player_name):         # constructor
        self.player_name = player_name       # instance attribute (unique)
```

---

## 5. Common Mistakes / What Not to Do

| Mistake | Why It Fails |
|---------|--------------|
| Defining class attribute inside `__init__` | Creates an instance attribute, not shared |
| Using `Pet` instead of `Pet()` for instantiation | `Pet` is the class, `Pet()` creates an object |
| Forgetting shadowing behavior | Instance attributes hide class attributes of the same name |
| Choosing wrong storage location | Per-object data should be instance, shared data should be class |

---

## 6. Open-Note Review

**Syntax Comparison**
```python
class ClassName:
    CLASS_ATTR = value              # class attribute (shared)

    def __init__(self, value):
        self.instance_attr = value  # instance attribute (unique)
```

**Shadowing Pattern**
```python
class Pet:
    species = "dog"

pet = Pet()
pet.species = "wolf"  # creates instance attribute, shadows class
```

**Decision Rule**
> If the value is usually the same for all objects → class attribute. If different for each object → instance attribute.

**Examples of Each**
- **Class attributes:** `default_food`, `manufacturer`, `screen_width`, `global_population`
- **Instance attributes:** `name`, `age`, `color`, `microchip_id`, `license_plate`

---

## 7. Final Takeaway

Instance attributes store per-object data (defined with `self.attribute` in `__init__`), while class attributes store shared data (defined in the class body). When an instance attribute has the same name as a class attribute, it shadows the class attribute for that object. Choose class attributes for values shared across all instances, and instance attributes for values unique to each object.

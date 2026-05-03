# Class-Level Basics: Attributes

## 1. Lesson Focus
Introduces **class attributes** — data stored on the class itself rather than on individual instances. All instances share the same class attribute value, which can be changed once and seen by all objects.

---

## 2. Core Concepts

### Class Attribute
**Definition:** Data stored on the class itself, shared by all instances. Defined in the class body, outside any method.

**Syntax:**
```python
class ClassName:
    class_attribute = value          # class attribute (shared)

    def __init__(self, instance_attr):
        self.instance_attr = instance_attr  # instance attribute (unique per object)
```

### Instance vs Class Attributes
| Attribute Type | Stored On | Copies | Shared? |
|----------------|-----------|--------|---------|
| Instance | Each object | One per object | No |
| Class | The class | One total | Yes, by all instances |

### Accessing Class Attributes
```python
ClassName.attribute          # Access directly on class
instance.attribute          # Access via instance (Python looks up to class)
```

When you access `instance.attribute`, Python first checks the instance. If not found, it looks up to the class.

---

## 3. Key Details to Remember

- **Class attributes are shared:** One copy exists, all instances see the same value
- **Defined outside methods:** Class attributes go in the class body, not inside `__init__` or other methods
- **Access via class or instance:** Both `ClassName.attr` and `instance.attr` work
- **Change once, affects all:** Modifying a class attribute updates what every instance sees
- **Use for shared data:** Good for constants, version numbers, settings common to all instances

---

## 4. Examples

### GameCharacter with Class Attributes
```python
class GameCharacter:                       # class representing game characters
    game_version = "1.0"                   # class attribute (shared)
    game_world = "Earth"                   # class attribute (shared)

    def __init__(self, name, health):      # constructor
        self.name = name                   # instance attribute (unique)
        self.health = health               # instance attribute (unique)

hero = GameCharacter("Hero", 100)
villain = GameCharacter("Villain", 80)

print(GameCharacter.game_version)         # Output: 1.0 (direct class access)
print(hero.game_version)                   # Output: 1.0 (via instance)
print(villain.game_version)                # Output: 1.0 (via instance)
```

### Changing Class Attribute
```python
GameCharacter.game_version = "2.0"         # change once on the class

print(hero.game_version)                   # Output: 2.0
print(villain.game_version)                # Output: 2.0
# Both instances now see the updated value
```

### Multiple Class Attributes
```python
class GameCharacter:
    game_version = "1.0"
    game_world = "Earth"

hero = GameCharacter()
villain = GameCharacter()
sidekick = GameCharacter()

print(hero.game_world)                     # Output: Earth
print(villain.game_world)                  # Output: Earth
print(sidekick.game_world)                 # Output: Earth
# All three read the same shared value
```

---

## 5. Common Mistakes / What Not to Do

| Mistake | Why It Fails |
|---------|--------------|
| Defining class attribute inside `__init__` | Creates an instance attribute, not a class attribute |
| Expecting instances to have separate copies | Class attributes are shared by design |
| Confusing access patterns | `instance.attr` works but reads from the class, not the instance |

---

## 6. Open-Note Review

**Class Attribute Syntax**
```python
class ClassName:
    CLASS_ATTR = value          # defined outside methods, shared by all instances

    def __init__(self):
        self.instance_attr = value  # unique per instance
```

**Access Patterns**
```python
ClassName.CLASS_ATTR       # direct class access
instance.CLASS_ATTR        # instance access (looks up to class)
```

**Key Rule**
> A class attribute is one shared value stored on the class. All instances read the same value, and changing it on the class updates what every instance sees.

---

## 7. Final Takeaway

Class attributes are data stored on the class itself, shared by all instances. Define them in the class body outside any method. All instances access the same copy, and modifying a class attribute updates the value for every object simultaneously.

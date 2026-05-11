# PY103 Week 9 - Wrap-up I: Pet Manager System

## 1. Lesson Focus
This wrap-up lesson integrates all OOP concepts learned so far into a single cohesive system: a Pet Manager that demonstrates encapsulation, inheritance, method overriding, composition, polymorphism, and `__str__` working together.

## 2. Core Concepts
- **Encapsulation**: Protected attributes (`_name`, `_indoor`) with getters and setters for controlled access.
- **Inheritance**: Dog and Cat inherit from Pet, reusing base class functionality.
- **Method Overriding**: Subclasses replace parent methods (`speak()`, `__str__()`) with their own implementations.
- **Composition**: PetManager contains a list of Pet objects (has-a relationship).
- **Polymorphism**: PetManager loops over mixed pet types and calls the same method (`speak()`) on each; Python selects the correct implementation based on actual object type.
- **`__str__` Methods**: Each class provides human-readable string representation.

## 3. Key Details to Remember
- **Constructor arguments**: Values in parentheses when creating an object match `__init__` parameters by position (e.g., `Dog("Smooky", "Corgie")` → `name="Smooky", breed="Corgie"`).
- **Protected attributes**: Use underscore prefix (`_name`) to signal internal data; update through setters for validation.
- **Overriding syntax**: Child class defines method with same name as parent to replace behavior.
- **Polymorphic loop**: Call same method on different objects without type-checking; trust that method exists on all objects in the collection.
- **Composition pattern**: Manager class stores objects in a list attribute and provides methods to manage them.

## 4. Complete System Example

```python
class Pet:
    def __init__(self, name):
        self._name = name

    def get_name(self):
        return self._name

    def set_name(self, new_name):
        if new_name != "":
            self._name = new_name

    def speak(self):
        return "..."

    def __str__(self):
        return f"Pet named {self._name}"


class Dog(Pet):
    def __init__(self, name, breed):
        self._name = name
        self.breed = breed

    def speak(self):
        return f"Woof! I'm {self._name} the {self.breed}"

    def __str__(self):
        return f"Dog named {self._name} (breed: {self.breed})"


class Cat(Pet):
    def __init__(self, name, indoor):
        self._name = name
        self._indoor = indoor

    def speak(self):
        if self._indoor:
            return f"Meow! I'm {self._name} and I'm an indoor cat."
        else:
            return f"Meow! I'm {self._name} and I'm an outdoor cat."

    def __str__(self):
        return f"Cat named {self._name} (indoor: {self._indoor})"


class PetManager:
    def __init__(self):
        self._pets = []

    def add_pet(self, pet):
        self._pets.append(pet)

    def make_all_pets_speak(self):
        for pet in self._pets:
            print(pet.speak())

    def __str__(self):
        result = "Pets in manager:\n"
        for pet in self._pets:
            result += str(pet) + "\n"
        return result


# ---- main ----
p2 = Dog("Smooky", "Corgie")
p3 = Cat("Whiskers", True)

manager = PetManager()
manager.add_pet(p2)
manager.add_pet(p3)

print(manager)
manager.make_all_pets_speak()
```

**Output**:
```
Pets in manager:
Dog named Smooky (breed: Corgie)
Cat named Whiskers (indoor: True)

Woof! I'm Smooky the Corgie
Meow! I'm Whiskers and I'm an indoor cat.
```

## 5. How Each Concept Appears in the System

### Encapsulation
- Pet uses `_name` (protected attribute)
- `get_name()` and `set_name()` control access
- Setter validates input (rejects empty names)

### Inheritance
- `class Dog(Pet):` and `class Cat(Pet):`
- Both inherit `_name` and getter/setter from Pet
- Each adds its own attributes (`breed`, `_indoor`)

### Method Overriding
- Dog overrides `speak()` to return dog-specific message
- Cat overrides `speak()` with conditional indoor/outdoor message
- Both override `__str__()` for custom string representation

### Composition
- PetManager has `_pets = []` (contains pet objects)
- `add_pet()` method manages the collection
- Manager is not a Pet; it contains Pets (has-a relationship)

### Polymorphism
- `make_all_pets_speak()` loops over `_pets`
- Calls `pet.speak()` on each object without type-checking
- Dog objects run Dog's `speak()`, Cat objects run Cat's `speak()`
- Manager doesn't need to know which type each pet is

## 6. Constructor Argument Matching

When creating objects, arguments in parentheses match `__init__` parameters by position:

```python
Dog("Smooky", "Corgie")  # name="Smooky", breed="Corgie"
Cat("Whiskers", True)    # name="Whiskers", indoor=True
Pet("Koko")             # name="Koko"
```

Alternative: keyword arguments (order doesn't matter):
```python
Dog(name="Smooky", breed="Corgie")
```

## 7. Common Mistakes / What Not to Do
- **Incorrect argument order**: `Dog("Corgie", "Smooky")` would assign breed to name and name to breed.
- **Using `super()` when not allowed**: In this exercise, directly set `self._name = name` instead of `super().__init__(name)`.
- **Type-checking in polymorphic loop**: Writing `if type(pet) is Dog:` inside `make_all_pets_speak()` defeats polymorphism.
- **Forgetting `__str__` return**: Method must return a string, not print directly.
- **Public instead of protected**: Using `self.name` instead of `self._name` breaks encapsulation convention.

## 8. Open-Note Review
- **Encapsulation**: Protected attributes with getters/setters for controlled access
- **Inheritance**: Child classes reuse parent code via `class Child(Parent):`
- **Overriding**: Child methods with same name replace parent implementation
- **Composition**: Manager class contains objects in a list (has-a relationship)
- **Polymorphism**: Loop calls same method on different objects; Python selects correct version
- **`__str__`**: Human-readable string representation for `print()` output
- **Constructor arguments**: Parentheses values match `__init__` parameters by position

## 9. Final Takeaway
Object-oriented programming concepts work together in integrated systems. Encapsulation protects state, inheritance reuses code, overriding customizes behavior, composition manages collections, polymorphism simplifies loops over mixed types, and `__str__` makes output readable. Understanding how these patterns combine is key to designing clean, maintainable OOP systems.

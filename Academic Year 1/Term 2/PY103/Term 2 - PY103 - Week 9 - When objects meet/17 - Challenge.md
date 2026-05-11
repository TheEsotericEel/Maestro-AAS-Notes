# PY103 Week 9 - Challenge: OOP Concepts Review

## 1. Lesson Focus
This challenge tests understanding of key object-oriented programming concepts: encapsulation with getters/setters, inheritance and overriding, composition vs inheritance, polymorphism, and the `__str__` method for human-readable output.

## 2. Core Concepts
- **Encapsulation with Getters**: Use internal attributes (underscore prefix) with getter methods to control read access to object state.
- **Setters with Validation**: Use setter methods to enforce rules before updating internal state (e.g., rejecting negative values).
- **Inheritance and Overriding**: Child classes can override parent methods to provide their own implementation.
- **Composition vs Inheritance**: Use "has-a" relationships (composition) when one object contains another, and "is-a" relationships (inheritance) when one class is a type of another.
- **Polymorphism**: The same method call produces different behaviors depending on the actual object type.
- **`__str__` Method**: Provides human-readable string representation for objects when printed.

## 3. Key Details to Remember
- **Getters**: Use `get_attribute()` methods instead of direct access to `_attribute` for controlled read access.
- **Setters**: Use `set_attribute(value)` methods with validation logic instead of direct assignment like `obj._attribute = value`.
- **Overriding**: Child class method with same name as parent replaces parent's implementation for that child.
- **Composition decision**: "X has a Y" → composition (store Y as attribute in X). "X is a type of Y" → inheritance (class X(Y)).
- **Polymorphism in loops**: Call the same method on different object types in a list; each runs its own implementation.
- **`__str__` syntax**: Exactly `def __str__(self):` with two underscores on each side.

## 4. Challenge Questions and Answers

### Question 1: Encapsulation (Getters)
**Scenario**: Want outside code to read a pet's age but not change it directly.

**Better design**:
- B) Make age underscored (`_age`) and provide a `get_age()` method

**Reasoning**: Encapsulation controls access — getters provide read-only access to internal attributes.

### Question 2: Setters & Validation
**Scenario**: Pet class with `_age` and a setter that rejects negative values.

**Better way to update age**:
- B) `pet.set_age(-3)`

**Reasoning**: Using the setter allows the class to enforce its validation rules (rejecting negative ages).

### Question 3: Inheritance & Overriding
**Code**:
```python
class Pet:
    def speak(self):
        return "some sound"

class Dog(Pet):
    def speak(self):
        return "woof"

buddy = Dog()
print(buddy.speak())
```

**Output**: B) `woof`

**Reasoning**: Dog overrides `speak()`, so Python uses the Dog version for Dog objects.

### Question 4: Composition vs Inheritance
**Scenario**: Playlist groups many songs, Song has title and artist.

**Better design**:
- B) `class Playlist:` with `self.songs = []` inside, because a playlist has songs

**Reasoning**: "Playlist has songs" is a has-a relationship → composition, not inheritance.

### Question 5: Polymorphism
**Code**:
```python
class Pet:
    def speak(self):
        return "some sound"

class Dog(Pet):
    def speak(self):
        return "woof"

class Cat(Pet):
    def speak(self):
        return "meow"

pets = [Dog(), Cat(), Dog()]

for pet in pets:
    print(pet.speak())
```

**Output**: B)
```
woof
meow
woof
```

**Reasoning**: Polymorphism — same method call (`speak()`), different behavior based on actual object type.

### Question 6: `__str__` for Human-Friendly Output
**Code**:
```python
class Pet:
    def __init__(self, name, age):
        self._name = name
        self._age = age

    def __str__(self):
        return f"{self._name} ({self._age} years old)"

pet = Pet("Luna", 3)
print(pet)
```

**Output**: B) `Luna (3 years old)`

**Reasoning**: `__str__` returns a human-readable string that `print()` uses instead of the default representation.

## 5. Common Mistakes / What Not to Do
- **Direct attribute access**: Using `pet._age = value` instead of `pet.set_age(value)` bypasses validation.
- **Forcing inheritance on has-a relationships**: Using `class Playlist(Song):` when a playlist is not a type of song.
- **Confusing polymorphism output**: Expecting the same output for all objects when different types override the method.
- **Incorrect `__str__` syntax**: Writing `__str_` (missing underscore) instead of `__str__`.
- **Not returning from `__str__`**: The method must return a string, not print directly.

## 6. Open-Note Review
- **Encapsulation**: Use getters/setters for controlled access to internal attributes
- **Setters**: Include validation logic to enforce rules before state changes
- **Overriding**: Child methods with same name replace parent implementation
- **Composition**: "has-a" → store as attribute; Inheritance: "is-a" → `class Child(Parent)`
- **Polymorphism**: Same method call, different behavior based on object type
- **`__str__`**: Human-readable string representation for `print()` output

## 7. Final Takeaway
Object-oriented design requires choosing the right pattern for each relationship: getters/setters for encapsulation, inheritance for is-a relationships, composition for has-a relationships, overriding for customizing behavior, polymorphism for uniform interfaces with diverse implementations, and `__str__` for human-readable object output.

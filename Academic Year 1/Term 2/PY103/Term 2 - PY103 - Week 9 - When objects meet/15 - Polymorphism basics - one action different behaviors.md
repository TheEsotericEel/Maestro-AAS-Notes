# Polymorphism Basics: One Action, Different Behaviors

## 1. Lesson Focus
Polymorphism allows the same method call to produce different behaviors depending on the actual type of the object. This eliminates long if/elif chains and makes code more flexible and maintainable.

## 2. Core Concepts
- **Polymorphism**: Calling the same method (same name, same way) on different object types, where each type runs its own implementation.
- **Method Overriding**: Subclasses define their own version of a parent method, enabling polymorphic behavior.
- **Dynamic Dispatch**: Python chooses which method implementation to run based on the actual object type at runtime, not the variable name.
- **Simplified Logic**: Polymorphism replaces type-checking if/elif chains with a single uniform method call.

## 3. Key Details to Remember
- Same method call (`obj.method()`) can produce different results based on object type
- Python looks at the real object type each time, not the variable name
- Works through method overriding in subclasses
- Eliminates need for type-checking (`if type(obj) is Class:`) chains
- New types "just work" as long as they implement the expected method
- Loop over mixed-type collections and call the same method on each item

## 4. How It Works

### Without Polymorphism (Type-Checking Chain)
```python
for pet in pets:
    if type(pet) is Dog:
        pet.bark()
    elif type(pet) is Cat:
        pet.meow()
    elif type(pet) is Hamster:
        pet.squeak()
    # must add more for each new type
```

### With Polymorphism (Uniform Call)
```python
for pet in pets:
    pet.speak()  # Each pet type runs its own speak()
```

### Python's Runtime Selection
1. Method is called on an object
2. Python checks the object's actual class
3. If the class has the method, it runs that version
4. If not, it checks parent classes (inheritance chain)
5. The first matching method found is executed

## 5. Examples

### Example 1: Pets with Polymorphic speak()
```python
class Pet:
    def speak(self):
        print("Some generic pet sound")


class Dog(Pet):
    def speak(self):
        print("Woof!")


class Cat(Pet):
    def speak(self):
        print("Meow!")


class Hamster(Pet):
    def speak(self):
        print("Squeak!")


# ---- main ----
pets = [Dog(), Hamster(), Cat()]

for pet in pets:
    pet.speak()
# Output:
# Woof!
# Squeak!
# Meow!
```

### Example 2: Instruments with Polymorphic play()
```python
class Instrument:
    def play(self):
        print("Some instrument sound")


class Guitar(Instrument):
    def play(self):
        print("Strum")


class Drum(Instrument):
    def play(self):
        print("Boom")


# ---- main ----
instruments = [Guitar(), Drum(), Guitar()]

for instrument in instruments:
    instrument.play()
# Output:
# Strum
# Boom
# Strum
```

### Example 3: Mixed Parent and Child Types
```python
class Instrument:
    def play(self):
        print("Some instrument sound")


class Guitar(Instrument):
    def play(self):
        print("Strum")


class Drum(Instrument):
    def play(self):
        print("Boom")


# ---- main ----
instruments = [Instrument(), Drum(), Guitar()]

for instrument in instruments:
    instrument.play()
# Output:
# Some instrument sound
# Boom
# Strum
```

## 6. Common Mistakes / What Not to Do
- **Using type-checking instead of polymorphism**: Writing `if type(obj) is Class:` chains when polymorphism would be cleaner.
- **Assuming variable name determines behavior**: The variable name does not matter; only the actual object type determines which method runs.
- **Forgetting to implement the method**: If a subclass doesn't override the method, the parent version runs (or an error occurs if no parent has it).
- **Thinking all objects must be same type**: Polymorphism works specifically with mixed-type collections where all types share a common interface (method name).

## 7. Open-Note Review
- Polymorphism = same method call, different behavior based on object type
- Enabled by method overriding in subclasses
- Python selects method implementation at runtime based on actual object type
- Replaces type-checking if/elif chains with uniform method calls
- New types automatically work if they implement the expected method
- Loop pattern: `for item in items: item.method()`

## 8. Final Takeaway
Polymorphism allows the same method call to produce different behaviors depending on the object type. By overriding methods in subclasses and calling the same method name on different objects, you eliminate type-checking chains and write cleaner, more flexible code that automatically accommodates new types.

# Inheritance: Method Overriding

## 1. Lesson Focus
Method overriding allows a child class to replace a parent class method with its own implementation. When a child class defines a method with the same name as the parent, Python uses the child's version instead of the parent's.

## 2. Core Concepts
- **Method Overriding**: A child class defines a method with the same name as a parent class method, replacing the parent's behavior with its own.
- **First-Stop Rule**: When calling a method, Python checks the object's own class first. If it finds the method there, it runs that version and stops looking.
- **Search Path**: Python searches upward through the inheritance chain (object's class → parent → grandparent) only if needed.

## 3. Key Details to Remember
- Child classes can override parent methods by defining a method with the same name
- Python always uses the version in the object's actual class, not the variable name
- The search starts at the object's class and moves upward only if no match is found
- Multiple subclasses can each override the same parent method differently
- Inheritance chains can be multiple levels deep (e.g., LoudDog → Dog → Pet)

## 4. How It Works

### Basic Overriding Pattern
```python
class Pet:
    def speak(self):
        print("Some generic pet sound")

class Dog(Pet):
    def speak(self):
        print("Woof!")
```
When `Dog().speak()` is called, Python uses `Dog.speak()`, not `Pet.speak()`.

### Python's Search Rule
1. Check the object's own class first
2. If the method is found, run it and stop
3. If not found, check the parent class
4. Continue upward through the inheritance chain until found

## 5. Examples

### Example 1: Pet, Dog, and Cat with Different Sounds
```python
class Pet:
    def __init__(self, name):
        self.name = name

    def speak(self):
        """Make a generic pet sound."""
        print("Some generic pet sound")


class Dog(Pet):
    def speak(self):
        """Make a dog sound: woof!"""
        print("Woof!")


class Cat(Pet):
    def speak(self):
        """Make a cat sound: meow!"""
        print("Meow!")


# ---- main ----
pet = Pet("Blob")
dog = Dog("Fido")
cat = Cat("Whiskers")

pet.speak()  # Output: Some generic pet sound
dog.speak()  # Output: Woof!
cat.speak()  # Output: Meow!
```

### Example 2: Multi-Level Inheritance Chain
```python
class Pet:
    def speak(self):
        print("Some generic pet sound")


class Dog(Pet):
    def speak(self):
        print("Woof!")


class LoudDog(Dog):
    def speak(self):
        print("WOOF!!!")


# ---- main ----
animal = LoudDog()
animal.speak()  # Output: WOOF!!!
```

### Example 4: Adding Hamster Subclass
```python
class Pet:
    def __init__(self, name):
        self.name = name

    def speak(self):
        """Make a generic pet sound."""
        print("Some generic pet sound")


class Dog(Pet):
    def speak(self):
        """Make a dog sound: woof!"""
        print("Woof!")


class Cat(Pet):
    def speak(self):
        """Make a cat sound: meow!"""
        print("Meow!")


class Hamster(Pet):
    def speak(self):
        """Make a hamster sound: squeak!"""
        print("Squeak!")


# ---- main ----
pet = Pet("Blob")
dog = Dog("Fido")
cat = Cat("Whiskers")
hammy = Hamster("Hammy")

pet.speak()   # Output: Some generic pet sound
dog.speak()   # Output: Woof!
cat.speak()   # Output: Meow!
hammy.speak() # Output: Squeak!
```

## 6. Common Mistakes / What Not to Do
- **Assuming variable name matters**: The variable name (`animal`, `pet`, `dog`) does not determine which method runs. Only the object's actual class matters.
- **Thinking all versions run**: Python does not run all versions in the chain. It runs only the first one found.
- **Confusing inheritance direction**: Python searches from child upward to parent, not the other way around.
- **Forgetting docstrings**: Overridden methods should still have clear docstrings explaining their specific behavior.

## 7. Open-Note Review
- Overriding: child class replaces parent method with same name
- First-stop rule: Python checks object's class first, then moves upward
- Object's actual class determines which method runs, not variable name
- Multiple subclasses can override the same parent method differently
- Search path: object's class → parent → grandparent (stops at first match)
- Inheritance chains can be multiple levels deep

## 8. Final Takeaway
When you call a method on an object, Python uses the first version it finds, starting from the object's own class and moving up to parent classes only if needed. This allows child classes to customize behavior inherited from parents.

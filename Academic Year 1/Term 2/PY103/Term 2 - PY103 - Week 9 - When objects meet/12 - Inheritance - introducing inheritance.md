# Inheritance: Introducing Inheritance

## 1. Lesson Focus
Inheritance allows a child class to automatically reuse all code from a parent class, avoiding duplication. Instead of rewriting methods and attributes, the child class inherits them and can use them immediately.

## 2. Core Concepts
- **Inheritance**: A child class (subclass) reuses code from a parent class (base class) without rewriting it.
- **Parent Class (Base Class)**: The class that provides the shared code and attributes.
- **Child Class (Subclass)**: The class that inherits from the parent and gets all its functionality for free.
- **Code Reuse**: Child classes automatically receive all methods and attributes defined in the parent class.

## 3. Key Details to Remember
- Python inheritance syntax: `class Child(Parent):`
- Child classes can use parent methods without rewriting them
- Multiple child classes can inherit from the same parent
- The child class body can be empty (`pass`) if it only needs inherited behavior
- Inheritance avoids code duplication across similar classes

## 4. How It Works

### Defining a Parent Class
```python
class Pet:
    """Parent class for all pets."""

    def __init__(self, name):
        self.name = name

    def eat(self):
        print(f"{self.name} is eating.")
```

### Creating a Child Class
```python
class Dog(Pet):
    """Child class that inherits from Pet."""
    pass  # no extra code needed
```

### Using Inherited Methods
```python
my_dog = Dog("Rex")
my_dog.eat()  # Uses Pet's eat() method
```

## 5. Examples

### Example 1: Pet with Dog and Cat
```python
class Pet:
    """Parent class for all pets."""

    def __init__(self, name):
        self.name = name

    def eat(self):
        print(f"{self.name} is eating.")


class Dog(Pet):
    """Child class that inherits from Pet."""
    pass


class Cat(Pet):
    """Child class that inherits from Pet."""
    pass


# ---- main ----
my_dog = Dog("Rex")
my_dog.eat()  # Output: Rex is eating.

my_cat = Cat("Mittens")
my_cat.eat()  # Output: Mittens is eating.
```

### Example 2: Vehicle and Bicycle
```python
class Vehicle:
    """Parent class for all vehicles."""

    def __init__(self, brand):
        self.brand = brand

    def start(self):
        print(f"{self.brand} is starting.")


class Bicycle(Vehicle):
    """Child class that inherits from Vehicle."""
    pass


# ---- main ----
my_bike = Bicycle("Trek")
my_bike.start()  # Output: Trek is starting.
```

### Example 3: Multiple Children from One Parent
```python
class Animal:
    """Parent class for all animals."""

    def __init__(self, species):
        self.species = species

    def speak(self):
        print(f"{self.species} makes a sound.")


class Dog(Animal):
    pass


class Cat(Animal):
    pass


class Bird(Animal):
    pass


# ---- main ----
dog = Dog("Dog")
cat = Cat("Cat")
bird = Bird("Bird")

dog.speak()   # Output: Dog makes a sound.
cat.speak()   # Output: Cat makes a sound.
bird.speak()  # Output: Bird makes a sound.
```

## 6. Common Mistakes / What Not to Do
- **Wrong syntax**: Using `class Child extends Parent:` (Java-style) instead of `class Child(Parent):` (Python-style).
- **Reversing order**: Writing `class Parent(Child):` when you mean the child to inherit from the parent.
- **Rewriting inherited code**: Defining methods in the child class that already exist identically in the parent when inheritance would suffice.
- **Forgetting pass**: Leaving the child class body empty without `pass` causes a syntax error.

## 7. Open-Note Review
- Inheritance lets child classes reuse parent class code without duplication
- Python syntax: `class Child(Parent):`
- Child classes automatically get all parent methods and attributes
- Multiple children can inherit from the same parent
- Child class can be empty (`pass`) if it only needs inherited behavior
- Avoids rewriting the same code across similar classes

## 8. Final Takeaway
Inheritance allows child classes to automatically reuse all code from a parent class. The child class is defined with `class Child(Parent):` and immediately gains access to all parent methods and attributes without rewriting them, eliminating code duplication.

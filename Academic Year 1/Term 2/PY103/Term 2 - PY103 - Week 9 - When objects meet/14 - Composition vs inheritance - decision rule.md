# Composition vs Inheritance: A Practical Decision Rule

## 1. Lesson Focus
This lesson teaches a simple decision rule for choosing between inheritance and composition based on the relationship between classes. Use the "is-a" test for inheritance and the "has-a" test for composition to design cleaner class relationships.

## 2. Core Concepts
- **Is-a Relationship**: When one class is a type or kind of another (e.g., Dog is a Pet). Signals inheritance.
- **Has-a Relationship**: When one class has, owns, or uses another (e.g., Car has an Engine). Signals composition.
- **Inheritance**: Child class inherits from parent class using `class Child(Parent):`
- **Composition**: One class contains an object of another class as an attribute (e.g., `self.engine = Engine(...)`)

## 3. Key Details to Remember
- **Decision Rule**: Try the sentence "X is a type of Y" — if natural, use inheritance. Try "X has a Y" or "X uses a Y" — if natural, use composition.
- **Inheritance Syntax**: `class Child(Parent):` — child is a kind of parent
- **Composition Syntax**: `self.attribute = OtherClass(...)` — containing class has an instance of another class
- Both patterns can be used together in the same design
- The English sentence test helps clarify the intended relationship

## 4. How It Works

### Testing for Inheritance
Ask: "Does X sound like a type of Y?"
- Dog is a type of Pet → inheritance: `class Dog(Pet):`
- Car is a type of Vehicle → inheritance: `class Car(Vehicle):`
- Student is a type of Person → inheritance: `class Student(Person):`

### Testing for Composition
Ask: "Does X sound like it has, owns, or uses Y?"
- Car has an Engine → composition: `self.engine = Engine(...)`
- PetOwner has Pets → composition: `self.pets = []`
- Library has Books → composition: `self.books = []`

## 5. Examples

### Example 1: Pet Owner with Both Patterns
```python
class Pet:
    def __init__(self, name):
        self.name = name


class Dog(Pet):  # Inheritance: Dog is a Pet
    def bark(self):
        print(f"{self.name} says: Woof!")


class PetOwner:
    def __init__(self, owner_name):
        self.owner_name = owner_name
        self.pets = []  # Composition: owner has pets


# ---- main ----
owner = PetOwner("Alice")
owner.pets.append(Dog("Rex"))
```

### Example 2: Car with Engine (Composition)
```python
class Engine:
    def __init__(self, horsepower):
        self.horsepower = horsepower


class Car:
    def __init__(self, brand, horsepower):
        self.brand = brand
        self.engine = Engine(horsepower)  # Composition: Car has an Engine


# ---- main ----
car = Car("Toyota", 180)
print(car.engine.horsepower)  # Output: 180
```

### Example 3: Combined Inheritance and Composition
```python
class Engine:
    def __init__(self, horsepower):
        self.horsepower = horsepower


class Vehicle:
    pass


class Car(Vehicle):  # Inheritance: Car is a Vehicle
    def __init__(self, brand, horsepower):
        self.brand = brand
        self.engine = Engine(horsepower)  # Composition: Car has an Engine


# ---- main ----
car = Car("Toyota", 180)
print(car.engine.horsepower)  # Output: 180
```

### Example 4: Library and Books
```python
class Book:
    def __init__(self, title):
        self.title = title


class Library:
    def __init__(self, name):
        self.name = name
        self.books = []  # Composition: Library has Books


# ---- main ----
library = Library("City Library")
library.books.append(Book("Python Programming"))
```

## 6. Common Mistakes / What Not to Do
- **Forcing inheritance on has-a relationships**: Using `class Book(Library):` when a book is not a type of library. Use composition instead.
- **Using composition for is-a relationships**: Creating a separate object when inheritance better expresses the type relationship.
- **Confusing the test**: Remember to test both sentences ("is a type of" and "has a") to see which sounds natural.
- **Overusing inheritance**: Not every relationship needs inheritance; composition is often more flexible for "has-a" relationships.

## 7. Open-Note Review
- Use the English sentence test to decide between inheritance and composition
- "X is a type of Y" → inheritance: `class Child(Parent):`
- "X has a Y" or "X uses a Y" → composition: `self.attribute = OtherClass(...)`
- Inheritance expresses type relationships (is-a)
- Composition expresses containment relationships (has-a)
- Both patterns can be used together in the same design
- The natural-sounding sentence reveals the intended relationship

## 8. Final Takeaway
Choose inheritance when one class is a type of another (is-a relationship). Choose composition when one class has, owns, or uses another (has-a relationship). The simple English sentence test — "X is a type of Y" vs "X has a Y" — reliably indicates which pattern to use.

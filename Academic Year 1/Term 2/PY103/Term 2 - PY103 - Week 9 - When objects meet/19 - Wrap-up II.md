# PY103 Week 9 - Wrap-up II: OOP Challenge Review

## 1. Lesson Focus
This wrap-up lesson tests understanding of core OOP concepts through 8 quick challenge rounds covering objects, constructors, encapsulation, composition vs inheritance, polymorphism, class vs instance attributes, one-to-many relationships, and method overriding.

## 2. Core Concepts
- **Object Purpose**: Represents a real thing in the program with its own attributes (data) and methods (behavior).
- **Constructor & State Change**: `__init__` initializes object state; methods modify state over time.
- **Encapsulation**: Using underscore prefix (`_attribute`) signals internal data; direct external access breaks encapsulation.
- **Composition vs Inheritance**: "Has-a" relationships use composition (containment), "is-a" relationships use inheritance.
- **Polymorphism**: Same method call produces different behavior based on actual object type.
- **Class vs Instance Attributes**: Class attributes are shared by all instances; instance attributes are unique per object.
- **One-to-Many Relationships**: The "one" side stores a list of the "many" objects (e.g., Course stores students list).
- **Overriding vs New Method**: Overriding replaces a parent method (same name); adding a new method doesn't affect parent behavior.

## 3. Challenge Questions and Answers

### Round 1: Object Purpose
**Question**: In Python OOP, what is the main purpose of an object?

**Answer**: An object represents a real thing in the program with its own attributes and methods.

### Round 2: Constructor & State Change
**Code**:
```python
class BankAccount:
    def __init__(self, owner, balance):
        self.owner = owner
        self.balance = balance

    def deposit(self, amount):
        self.balance = self.balance + amount

account = BankAccount("Alex", 100)
account.deposit(40)
account.deposit(10)
print(account.balance)
```

**Output**: `150`

**Reasoning**: Starting balance 100 + deposit 40 + deposit 10 = 150.

### Round 3: Encapsulation Check
**Code**:
```python
class Player:
    def __init__(self, name):
        self.name = name
        self._score = 0

player = Player("Sam")
player._score = -50
```

**Question**: Is this respecting or breaking encapsulation?

**Answer**: Breaking encapsulation, because the score is being changed outside of the class.

**Reasoning**: The underscore convention signals internal use; direct external access goes around that protection.

### Round 4: Composition vs Inheritance
**Scenario**: Library has many Book objects. Book does not behave like a kind of Library.

**Answer**: Composition

**Reasoning**: "Library has books" is a has-a relationship → composition (Library stores Book objects in a list).

### Round 5: Polymorphism in a Loop
**Code**:
```python
class Animal:
    def speak(self):
        return "..."

class Dog(Animal):
    def speak(self):
        return "woof"

class Cat(Animal):
    def speak(self):
        return "meow"

pets = [Dog(), Cat(), Dog()]

for p in pets:
    print(p.speak())
```

**Output**:
```
woof
meow
woof
```

**Reasoning**: Polymorphism — each object runs its own `speak()` implementation based on its actual type.

### Round 6: Class vs Instance Attributes
**Code**:
```python
class Robot:
    kind = "helper"

    def __init__(self, name):
        self.name = name

r1 = Robot("R2D2")
r2 = Robot("C3PO")
Robot.kind = "worker"
print(r1.kind)
print(r2.kind)
```

**Output**:
```
worker
worker
```

**Reasoning**: `kind` is a class attribute shared by all instances; changing `Robot.kind` affects all instances.

### Round 7: One-to-Many Relationship
**Scenario**: Course has many Student objects enrolled.

**Answer**: The Course class should store a list of enrolled students in an attribute like `students`.

**Reasoning**: The "one" side (Course) holds the collection of the "many" objects (Students).

### Round 8: Overriding vs New Method
**Code**:
```python
class Ticket:
    def price(self):
        return 10

class VipTicket(Ticket):
    def price(self):
        return 25

class BackstagePass(Ticket):
    def backstage_price(self):
        return 50

tickets = [Ticket(), VipTicket(), BackstagePass()]

for t in tickets:
    print(t.price())
```

**Output**:
```
10
25
10
```

**Reasoning**: `VipTicket` overrides `price()` (returns 25). `BackstagePass` adds a new method `backstage_price()` but does not override `price()`, so it inherits `Ticket.price()` (returns 10).

## 4. Key Patterns to Remember

### Encapsulation
- Use `_attribute` to signal internal data
- External code should use getters/setters, not direct access
- Direct assignment to `_attribute` from outside breaks encapsulation

### Composition vs Inheritance
- "X has a Y" → composition (X stores Y as attribute)
- "X is a type of Y" → inheritance (class X(Y))

### Polymorphism
- Loop calls same method on different object types
- Each object runs its own implementation
- No type-checking needed in the loop

### Class vs Instance Attributes
- Class attributes: defined outside `__init__`, shared by all instances
- Instance attributes: defined in `__init__` with `self.`, unique per object
- Changing class attribute affects all instances

### Overriding
- Child method with same name as parent replaces parent's implementation
- New method with different name doesn't affect parent behavior
- Child inherits parent methods it doesn't override

## 5. Common Mistakes / What Not to Do
- **Breaking encapsulation**: Directly accessing `_attribute` from outside the class instead of using getters/setters.
- **Wrong relationship type**: Using inheritance for has-a relationships (e.g., `class Playlist(Song)`) or composition for is-a relationships.
- **Type-checking in polymorphic loops**: Writing `if type(obj) is Class:` inside loops defeats polymorphism.
- **Confusing class/instance attributes**: Expecting instance attributes to be shared or class attributes to be unique.
- **Assuming new method overrides**: Adding a method with a different name doesn't replace parent behavior; must use exact same name to override.

## 6. Open-Note Review
- **Objects**: Bundle attributes (data) and methods (behavior) for real-world things
- **Encapsulation**: `_attribute` convention + getters/setters for controlled access
- **Composition**: Has-a → store as attribute in containing class
- **Inheritance**: Is-a → `class Child(Parent)`
- **Polymorphism**: Same method call, different behavior based on object type
- **Class attributes**: Shared by all instances; instance attributes: unique per object
- **One-to-many**: "One" side stores list of "many" objects
- **Overriding**: Same method name replaces parent; different name adds new method

## 7. Final Takeaway
Object-oriented programming combines multiple patterns: objects bundle data and behavior, encapsulation protects state through controlled access, composition models has-a relationships while inheritance models is-a relationships, polymorphism enables uniform interfaces with diverse implementations, class attributes are shared while instance attributes are unique, and overriding replaces parent behavior while new methods extend it without affecting existing functionality.

# Who Owns the State?

## 1. Lesson Focus
Deciding which class should own a method based on which class owns the data the method uses—keeping behavior with its data reduces bugs and improves code clarity.

## 2. Core Concepts
**Data + Behavior Together**: The object that owns the data should usually own the behavior that uses that data.

**State Ownership**: The class that holds attributes (state) should also hold methods that operate on those attributes.

**Delegation Pattern**: When logic needs to be moved, the original class can delegate to the data-owning class instead of reimplementing the logic.

**Stale Data Risk**: Methods that live away from their data risk using stale or incorrect data when references change.

## 3. Key Details to Remember
- Methods should live on the class that owns the data they use
- Reduces chance of using wrong or stale data
- Single source of truth for logic and data
- Easier to maintain—formula changes in one place
- Other objects can delegate to the data-owning object

## 4. Refactoring Pattern

**Move Method Pattern**:
```python
# Before: logic on wrong class
class PetOwner:
    def pet_bmi(self):
        return self.pet.weight / (self.pet.height ** 2)

# After: logic on data-owning class
class Pet:
    def bmi(self):
        return self.weight / (self.height ** 2)

class PetOwner:
    def pet_bmi(self):
        return self.pet.bmi()  # delegate
```

## 5. Examples

### Example 1: Pet BMI (Before)
```python
class Pet:
    def __init__(self, name, weight, height):
        self.name = name
        self.weight = weight
        self.height = height

class PetOwner:
    def __init__(self, owner_name, pet):
        self.owner_name = owner_name
        self.pet = pet

    def pet_bmi(self):
        # uses pet's data, but lives on PetOwner
        return self.pet.weight / (self.pet.height ** 2)
```

### Example 2: Pet BMI (After)
```python
class Pet:
    def __init__(self, name, weight, height):
        self.name = name
        self.weight = weight
        self.height = height

    def bmi(self):
        # logic lives where data lives
        return self.weight / (self.height ** 2)

class PetOwner:
    def __init__(self, owner_name, pet):
        self.owner_name = owner_name
        self.pet = pet

    def pet_bmi(self):
        return self.pet.bmi()  # delegate to Pet
```

### Example 3: Order Final Price (Before)
```python
class Order:
    def __init__(self, items_total, tax_rate):
        self.items_total = items_total
        self.tax_rate = tax_rate

class Customer:
    def __init__(self, name, order):
        self.name = name
        self.order = order

    def order_final_price(self):
        # uses order's data, but lives on Customer
        return self.order.items_total * (1 + self.order.tax_rate)
```

### Example 4: Order Final Price (After)
```python
class Order:
    def __init__(self, items_total, tax_rate):
        self.items_total = items_total
        self.tax_rate = tax_rate

    def final_price(self):
        return self.items_total * (1 + self.tax_rate)

class Customer:
    def __init__(self, name, order):
        self.name = name
        self.order = order

    def order_final_price(self):
        return self.order.final_price()  # delegate to Order
```

### Example 5: Bank Withdrawal
```python
class BankAccount:
    def __init__(self, balance):
        self.balance = balance

    def withdraw(self, amount):
        if amount <= self.balance:
            self.balance -= amount
            return True
        return False

class Customer:
    def __init__(self, name, account):
        self.name = name
        self.account = account

# Customer delegates to account
customer.account.withdraw(50)
```

## 6. Common Mistakes / What Not to Do
- **Logic on wrong class**: Placing methods on classes that don't own the data they use. Move methods to the data-owning class.
- **Reaching through references**: Using `self.pet.weight` instead of keeping logic on Pet. Delegate to `self.pet.method()`.
- **Duplicate logic**: Implementing the same calculation in multiple places. Keep single source of truth on data-owning class.
- **Stale data bugs**: When references change, methods on wrong classes may use old data. Methods on data-owning class always use current data.

## 7. Open-Note Review
- Object that owns data should own behavior that uses that data
- Methods should live where their data lives
- Reduces bugs from stale or wrong data
- Single place to update when logic changes
- Other objects can delegate instead of reimplementing
- Pattern: move method → use `self` inside → delegate from other classes

## 8. Final Takeaway
The object that owns the data should usually own the methods that use or change that data—this keeps logic with state, reduces bugs, and makes code clearer and easier to maintain.

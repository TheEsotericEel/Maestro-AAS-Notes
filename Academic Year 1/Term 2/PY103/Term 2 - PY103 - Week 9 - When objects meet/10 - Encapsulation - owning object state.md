# Encapsulation: Owning Object State

## 1. Lesson Focus
Encapsulation is the object-oriented principle that an object owns and controls access to its own data. Instead of allowing external code to directly modify internal attributes, the object provides controlled methods (getters) to read its state safely.

## 2. Core Concepts
- **Encapsulation**: An object owns its data and controls how other code can access it. The object acts as a protective bubble around its internal state.
- **Internal Attributes**: Attributes marked with a leading underscore (e.g., `_name`, `_hunger`, `_balance`) signal that they are internal data. Python does not enforce this, but it is a strong convention.
- **Getter Methods**: Methods whose sole purpose is to return a piece of internal data without allowing outside code to modify it directly. They provide a read-only window into object state.

## 3. Key Details to Remember
- Use a single underscore prefix (`_`) to mark attributes as internal by convention
- Getter methods should simply return the internal attribute value
- External code should call getters (e.g., `pet.get_name()`) instead of accessing internal attributes directly (e.g., `pet._name`)
- Encapsulation puts the object in control of how its data is accessed
- The underscore convention is not enforced by Python but is widely respected

## 4. How It Works

### Marking Internal Attributes
Add a leading underscore to attribute names in `__init__`:
```python
self._name = name        # internal attribute
self._hunger = hunger    # internal attribute
```

### Creating Getter Methods
Define methods that return internal attributes:
```python
def get_name(self):
    """Return the pet's name."""
    return self._name

def get_hunger(self):
    """Return the pet's hunger level."""
    return self._hunger
```

### Using Getters from External Code
Access object state through getters instead of direct attribute access:
```python
# Correct (encapsulated)
print(pet.get_name())

# Avoid (breaks encapsulation convention)
print(pet._name)
```

## 5. Examples

### Example 1: Pet Class with Encapsulation
```python
class Pet:
    """Represents a pet with a name and hunger level."""

    def __init__(self, name, hunger, happiness):
        """Initialize a new Pet with a name, hunger level, and happiness."""
        self._name = name        # internal attribute
        self._hunger = hunger    # internal attribute
        self._happiness = happiness  # internal attribute

    def get_name(self):
        """Return the pet's name."""
        return self._name

    def get_hunger(self):
        """Return the pet's hunger level."""
        return self._hunger

    def get_happiness(self):
        """Return the pet's happiness level."""
        return self._happiness


# ---- main ----
pet = Pet("Luna", 5, 80)
print(pet.get_name())      # Output: Luna
print(pet.get_hunger())    # Output: 5
print(pet.get_happiness()) # Output: 80
```

### Example 2: BankAccount Class with Encapsulation
```python
class BankAccount:
    """Represents a simple bank account."""

    def __init__(self, balance):
        """Initialize the account with a starting balance."""
        self._balance = balance   # internal attribute

    def get_balance(self):
        """Return the current account balance."""
        return self._balance


# ---- main ----
account = BankAccount(100)
print(account.get_balance())  # Output: 100
```

### Example 3: Player Class
```python
class Player:
    def __init__(self, score):
        self._score = score

    def get_score(self):
        return self._score

# Correct usage
player = Player(150)
print(player.get_score())  # Output: 150

# Avoid (breaks convention)
print(player._score)       # Discouraged
```

## 6. Common Mistakes / What Not to Do
- **Direct access to internal attributes**: Using `pet._name` instead of `pet.get_name()` breaks the encapsulation convention.
- **Forgetting the underscore**: Using `self.name` instead of `self._name` fails to signal that the attribute should be internal.
- **Not providing getters**: If you mark attributes as internal, you must provide getter methods for external code to read them.
- **Treating underscore as enforced security**: The underscore is a convention, not enforced access control. Python still allows direct access if code ignores the convention.

## 7. Open-Note Review
- Encapsulation means the object owns and controls access to its data
- Use underscore prefix (`_`) to mark internal attributes by convention
- Getter methods safely return internal state without allowing direct modification
- External code should use getters (e.g., `get_name()`) not direct attribute access (e.g., `_name`)
- The getter method itself is the encapsulation mechanism — it controls the door to internal data
- Common pattern: `def get_attribute(self): return self._attribute`

## 8. Final Takeaway
Encapsulation is implemented through internal attributes (underscore prefix) and getter methods. The object controls access to its data by providing methods that return internal state, while external code respects the convention by using those methods instead of reaching inside the object directly.

# Simple Invariants: What Must Always Stay True

## 1. Lesson Focus
Defining and enforcing object invariants—rules that must always be true about an object's state—to prevent bugs across multiple method calls.

## 2. Core Concepts
**Object Invariant**: A rule that must always be true about an object's state (e.g., battery charge always between 0 and 100).

**Enforcement Locations**: Invariants should be enforced in `__init__` (to prevent creating invalid objects) and in every method that changes state (mutators).

**Clamping (Auto-Correct)**: Silently fixing values that violate the invariant by pushing them back into the valid range.

**Assert (Fail Fast)**: Stopping the program with an error if the invariant is violated, useful during development to catch bugs early.

## 3. Key Details to Remember
- Invariants must be true at the end of every method call
- Enforce in `__init__` to prevent creating invalid objects
- Enforce in every mutator method that can change the invariant state
- Inside a method, state may temporarily go outside valid range
- By method end, state must be corrected back to valid range
- Clamping is good for user-facing code (stable, no crashes)
- Assert is good for development/testing (catches bugs early)

## 4. Implementation Patterns

**Clamping Pattern**:
```python
class Battery:
    def __init__(self, charge):
        self.charge = charge
        if self.charge < 0:
            self.charge = 0
        if self.charge > 100:
            self.charge = 100

    def add_charge(self, amount):
        self.charge += amount
        if self.charge < 0:
            self.charge = 0
        if self.charge > 100:
            self.charge = 100
```

**Assert Pattern**:
```python
class Battery:
    def __init__(self, charge):
        self.charge = charge
        assert 0 <= self.charge <= 100, "charge must be between 0 and 100"

    def add_charge(self, amount):
        self.charge += amount
        assert 0 <= self.charge <= 100, "charge must be between 0 and 100"
```

## 5. Examples

### Example 1: Battery with Clamping
```python
class Battery:
    def __init__(self, charge):
        self.charge = charge
        # clamp in __init__
        if self.charge < 0:
            self.charge = 0
        if self.charge > 100:
            self.charge = 100

    def add_charge(self, amount):
        self.charge += amount
        # clamp in mutator
        if self.charge < 0:
            self.charge = 0
        if self.charge > 100:
            self.charge = 100

# Usage
battery = Battery(50)
battery.add_charge(40)  # charge = 90
battery.add_charge(30)  # temporarily 120, clamped to 100
print(battery.charge)  # Output: 100
```

### Example 2: Battery with Assert
```python
class Battery:
    def __init__(self, charge):
        self.charge = charge
        assert 0 <= self.charge <= 100, "charge must be between 0 and 100"

    def add_charge(self, amount):
        self.charge += amount
        assert 0 <= self.charge <= 100, "charge must be between 0 and 100"

# If charge goes outside range, program stops with AssertionError
```

### Example 3: Multi-Method Sequence
```python
# With invariants enforced, later methods can trust valid state
battery = Battery(50)
battery.add_charge(50)    # ends at 100
log_status(battery)       # can trust charge is 0-100
battery.use_power(30)    # ends at 70
battery.add_charge(40)    # ends at 100 (clamped)
```

## 6. Common Mistakes / What Not to Do
- **Enforcing only in `__init__`**: Methods can still break the invariant later. Enforce in all mutators.
- **Enforcing only in some methods**: If one method lacks the check, invariants can be violated. Add to every mutator.
- **Trusting caller input**: Don't assume external code passes valid values. Always enforce invariants internally.
- **Forgetting to clamp after changes**: State may temporarily go outside range, but must be corrected before method returns.

## 7. Open-Note Review
- Invariant: rule that must always be true about object state
- Enforce in `__init__` and every mutator method
- Clamping: silently fix invalid values (good for user-facing code)
- Assert: fail loudly on violation (good for development/testing)
- State may temporarily go outside range during method
- By method end, state must be back in valid range
- Prevents weird bugs across multiple method calls

## 8. Final Takeaway
Enforce object invariants in `__init__` and every mutator method—this ensures the object's state is always valid at method boundaries, preventing bugs across multiple method calls.

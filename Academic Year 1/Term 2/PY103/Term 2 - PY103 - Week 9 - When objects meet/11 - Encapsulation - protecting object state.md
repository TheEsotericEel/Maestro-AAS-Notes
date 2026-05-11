# Encapsulation: Protecting Object State

## 1. Lesson Focus
This lesson teaches how to protect object state using setter methods with validation. Instead of allowing external code to directly modify internal attributes, setters act as controlled gates that can check, limit, or fix values before they are stored, preventing objects from entering invalid states.

## 2. Core Concepts
- **Setter Methods**: Methods whose job is to take a new value, optionally check or fix it, then store it in the object. They replace direct attribute assignment from external code.
- **Validation in Setters**: Checking incoming values before storing them. Invalid values can be refused (rejected) or fixed (clamped).
- **Clamping**: Fixing out-of-range values by pushing them back into the valid range (e.g., negative becomes 0, values above 100 become 100).
- **Refusing Invalid Values**: Simply exiting the method without updating the attribute when a value violates the rules.

## 3. Key Details to Remember
- All writes to internal attributes should go through setter methods
- Setters provide a single gate where validation logic lives
- Validation prevents objects from entering impossible or invalid states
- Two common patterns: refuse bad values (return early) or clamp them into valid range
- The underscore convention (`_balance`) signals internal data, but setters enforce the protection

## 4. How It Works

### Basic Setter Pattern
```python
def set_balance(self, new_balance):
    self._balance = new_balance
```
Instead of `account.balance = 100`, external code calls `account.set_balance(100)`.

### Refusing Invalid Values
```python
def set_balance(self, new_balance):
    if new_balance < 0:
        return  # refuse the change

    self._balance = new_balance
```
If the value is invalid, the method exits without changing the attribute.

### Clamping Values
```python
def set_charge(self, new_charge):
    if new_charge < 0:
        new_charge = 0
    if new_charge > 100:
        new_charge = 100

    self._charge = new_charge
```
Fix the incoming value first, then store the corrected value once.

## 5. Examples

### Example 1: Battery with Clamping (0–100%)
```python
class Battery:
    def __init__(self, charge):
        self._charge = charge  # 0–100

    def set_charge(self, new_charge):
        """Set battery charge, clamped between 0 and 100."""
        if new_charge < 0:
            new_charge = 0
        if new_charge > 100:
            new_charge = 100

        self._charge = new_charge


# ---- main ----
battery = Battery(50)

battery.set_charge(80)   # _charge becomes 80
battery.set_charge(-10)  # clamped up → _charge becomes 0
battery.set_charge(999)  # clamped down → _charge becomes 100
```

### Example 2: BankAccount with Refusal
```python
class BankAccount:
    def __init__(self, balance):
        self._balance = balance

    def set_balance(self, new_balance):
        """Set balance, refusing negative values."""
        if new_balance < 0:
            return  # refuse the change

        self._balance = new_balance


# ---- main ----
account = BankAccount(100)

account.set_balance(-50)  # refused, _balance stays 100
account.set_balance(200)  # accepted, _balance becomes 200
```

### Example 3: Combined Pattern
```python
class VolumeControl:
    def __init__(self, volume):
        self._volume = volume  # 0–10

    def set_volume(self, new_volume):
        """Set volume, clamped between 0 (mute) and 10 (max)."""
        if new_volume < 0:
            new_volume = 0
        if new_volume > 10:
            new_volume = 10

        self._volume = new_volume
```

## 6. Common Mistakes / What Not to Do
- **Direct attribute assignment**: External code doing `account._balance = 100` bypasses all protection. Use setters instead.
- **Storing before validation**: Assigning `self._balance = new_balance` before checking the value. Always validate or clamp first.
- **Reassigning instead of returning**: When refusing a change, use `return` to exit early rather than reassigning the old value. This signals intent clearly.
- **Forgetting validation**: A setter without validation provides no protection over direct assignment.

## 7. Open-Note Review
- Setters control how object state is changed from external code
- All writes should go through setters, not direct attribute assignment
- Two validation patterns: refuse invalid values (return early) or clamp into valid range
- Clamping fixes out-of-range values before storage
- Validation prevents objects from entering impossible states
- Pattern: check/fix first, then store once in one place

## 8. Final Takeaway
If an attribute should never be invalid, all writes should go through a setter that enforces the rules. Setters act as protective gates that can check, limit, or fix values before they touch internal state, ensuring objects never enter invalid or impossible states.

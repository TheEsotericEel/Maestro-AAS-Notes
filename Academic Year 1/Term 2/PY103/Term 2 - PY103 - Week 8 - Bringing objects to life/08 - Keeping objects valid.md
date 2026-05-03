# Keeping Objects Valid

## 1. Lesson Focus
Shows how to validate inputs inside `__init__` to ensure objects start life in a valid state, using safe fallback values to correct bad data before it becomes part of the object.

---

## 2. Core Concepts

### Constructor Validation
**Definition:** Checking and correcting input values inside `__init__` before storing them as attributes, ensuring the object is always created in a valid state.

**Purpose:** Prevent impossible values from being stored, avoiding bugs later in the program.

### Safe Fallback Values
**Definition:** A reasonable default value used to replace invalid input.

**Pattern:**
```python
if value < minimum:
    value = minimum
self.value = value
```

### Why Validate in `__init__`
- Objects start life in a valid state
- Prevents bugs from bad data propagating through the code
- Makes the rest of the code simpler and safer
- Similar to real-world forms that reject or auto-correct impossible values

---

## 3. Key Details to Remember

- **Validate before storing:** Check input values in `__init__` before assigning to `self.attribute`
- **Use safe fallbacks:** Replace invalid values with reasonable defaults
- **Objects born valid:** After `__init__` runs, the object should always satisfy your rules
- **Early prevention:** Fix bad data at creation time, not later

---

## 4. Examples

### BankAccount: Balance Must Be Non-Negative
```python
class BankAccount:                            # class representing a bank account
    def __init__(self, balance):             # constructor with balance parameter
        if balance < 0:                      # validate: balance must be >= 0
            balance = 0                      # safe fallback: use 0 if negative
        self.balance = balance              # store the validated value

account1 = BankAccount(200)                  # valid input, stays 200
account2 = BankAccount(-50)                  # invalid input, corrected to 0

print(account1.balance)                      # Output: 200
print(account2.balance)                      # Output: 0
```

### ConcertTicket: Minimum Price
```python
class ConcertTicket:                         # class for concert tickets
    def __init__(self, price):               # constructor with price parameter
        if price < 10:                       # validate: minimum price is 10
            price = 10                       # safe fallback: use 10 if too low
        self.price = price                  # store the validated value
```

### VideoPlayer: Volume Range (0-100)
```python
class VideoPlayer:                          # class for a video player
    def __init__(self, volume):              # constructor with volume parameter
        if volume < 0:                       # validate: minimum volume is 0
            volume = 0
        elif volume > 100:                   # validate: maximum volume is 100
            volume = 100                     # safe fallback: clamp to valid range
        self.volume = volume                # store the validated value

player1 = VideoPlayer(50)                    # already valid
player2 = VideoPlayer(-10)                   # too low, corrected to 0
player3 = VideoPlayer(150)                   # too high, corrected to 100

print(player1.volume)                       # Output: 50
print(player2.volume)                       # Output: 0
print(player3.volume)                       # Output: 100
```

### UserProfile: Minimum Age
```python
class UserProfile:                          # class for user profiles
    def __init__(self, age):                 # constructor with age parameter
        if age < 13:                        # validate: minimum age is 13
            age = 13                         # safe fallback: use 13 if too young
        self.age = age                       # store the validated value
```

---

## 5. Common Mistakes / What Not to Do

| Mistake | Why It Fails |
|---------|--------------|
| `self.balance = balance` without validation | Copies bad values directly into the object |
| Only printing the value | `print("balance is", balance)` doesn't prevent bad data |
| Using `input()` instead of validation | Reading from user doesn't check or fix values |
| Validating after storing | Store the validated value, not the raw input |

---

## 6. Open-Note Review

**Validation Pattern**
```python
def __init__(self, value):
    if value < minimum:          # check for invalid value
        value = minimum          # apply safe fallback
    self.value = value          # store the corrected value
```

**Range Validation Pattern**
```python
def __init__(self, value):
    if value < min:             # too low
        value = min
    elif value > max:           # too high
        value = max
    self.value = value
```

**Key Rule**
> Check inputs inside `__init__` and use safe fallback values to fix bad data before storing.

---

## 7. Final Takeaway

Validate inputs inside `__init__` to ensure objects start life in a valid state. Use safe fallback values to replace invalid inputs with reasonable defaults. This prevents impossible values from being stored, avoids bugs later, and makes the codebase safer and simpler.

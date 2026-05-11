# PY103 Week 9 - Challenge: Object State and Lists of Objects

## 1. Lesson Focus
This lesson tests understanding of object-oriented programming through two interactive puzzles:
- Tracking how methods change object attributes over time
- Reasoning about multiple objects stored in a list and updated via iteration

## 2. Core Concepts
- **Multiple instances of a class**: Each object has its own independent state
- **Object state changes**: Methods modify instance attributes over time
- **Iteration over objects**: Using loops to update multiple objects in a collection

## 3. Key Details to Remember
- Each object instance maintains its own separate attribute values
- Calling a method on one object does not affect other objects of the same class
- When iterating over a list of objects, each object is modified independently
- State changes are cumulative — each method call builds on the current state

## 4. How It Works

### Tracking Object State
- Create multiple instances with different initial values
- Call methods on specific instances to change their state
- Track each object's state separately through the sequence of operations

### Iterating Over Lists of Objects
- Store multiple object instances in a list
- Use a `for` loop to iterate through the list
- Call methods on each object in turn
- Each object's state changes independently based on the method logic

## 5. Examples

### Example 1: Object State with Toggle
```python
class Torch:
    def __init__(self, is_on):
        self.is_on = is_on

    def toggle(self):
        self.is_on = not self.is_on

torch_a = Torch(False)  # torch_a.is_on = False
torch_b = Torch(True)   # torch_b.is_on = True

torch_a.toggle()        # torch_a.is_on = True
torch_b.toggle()        # torch_b.is_on = False
torch_b.toggle()        # torch_b.is_on = True

print(torch_a.is_on, torch_b.is_on)  # Output: True True
```

**Reasoning:**
- `torch_a` toggled once: False → True
- `torch_b` toggled twice: True → False → True

### Example 2: List of Objects with Drain
```python
class Battery:
    def __init__(self, charge):
        self.charge = charge    # charge is an integer from 0 to 100

    def drain(self, amount):
        self.charge = self.charge - amount
        if self.charge < 0:
            self.charge = 0

b1 = Battery(50)
b2 = Battery(80)
b3 = Battery(30)

batteries = [b1, b2, b3]

for b in batteries:
    b.drain(20)

print(b1.charge, b2.charge, b3.charge)  # Output: 30 60 10
```

**Reasoning:**
- Each battery drains 20 independently
- `b1`: 50 - 20 = 30
- `b2`: 80 - 20 = 60
- `b3`: 30 - 20 = 10

## 6. Common Mistakes / What Not to Do
- **Assuming shared state**: Objects of the same class do not share attribute values
- **Forgetting cumulative changes**: State changes build on previous state, not original state
- **Confusing loop variable with original objects**: The loop variable `b` refers to each actual object, not a copy
- **Missing edge case handling**: The `drain` method includes a guard (`if self.charge < 0`) to prevent negative values

## 7. Open-Note Review
- Each object instance has independent state
- Methods modify the specific object they are called on
- Iterating over a list of objects applies operations to each object separately
- State changes are sequential and cumulative
- Always consider edge cases (e.g., preventing negative values)

## 8. Final Takeaway
Object-oriented programming requires tracking each object's state independently. When working with collections of objects, iteration allows you to apply operations uniformly while each object maintains its own separate state through the sequence of changes.

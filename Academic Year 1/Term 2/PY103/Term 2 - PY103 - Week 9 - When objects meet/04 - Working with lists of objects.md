# Working with Lists of Objects

## 1. Lesson Focus
Using for loops to iterate over lists of objects, accessing attributes and calling methods on each object within the loop.

## 2. Core Concepts
**Loop Variable is the Object**: When looping `for robot in robots:`, the variable `robot` is the full object with all its methods and attributes, not just a value.

**Attribute Access in Loop**: Use dot notation inside the loop to read attributes (e.g., `robot.name`, `robot.battery_level`).

**Method Calls in Loop**: Call object methods inside the loop (e.g., `robot.report()`, `robot.diagnose()`).

**Combining Operations**: Can call methods and read attributes in the same loop, and use conditionals based on attribute values.

## 3. Key Details to Remember
- `for item in items:` gives you each full object, not an index
- Use dot notation to access attributes and methods inside the loop
- Can combine method calls with conditional logic based on attributes
- Print statements inside loop vs. after loop have different effects

## 4. Implementation Pattern

**Basic Loop Pattern**:
```python
for object in objects:
    object.method()
```

**Attribute Access Pattern**:
```python
for object in objects:
    print(object.attribute)
```

**Combined Pattern**:
```python
for object in objects:
    object.method()
    if object.attribute < threshold:
        # do something
```

## 5. Examples

### Example 1: Accessing Attributes in Loop
```python
class Robot:
    def __init__(self, name, battery_level):
        self.name = name
        self.battery_level = battery_level

robots = [
    Robot("R2-D2", 80),
    Robot("C-3PO", 60),
    Robot("WALL-E", 30)
]

for robot in robots:
    print(robot.name, robot.battery_level)
# Output:
# R2-D2 80
# C-3PO 60
# WALL-E 30
```

### Example 2: Calling Methods in Loop
```python
class Robot:
    def __init__(self, name, battery_level):
        self.name = name
        self.battery_level = battery_level

    def report(self):
        print(f"{self.name} has {self.battery_level}% battery")

for robot in robots:
    robot.report()
```

### Example 3: Combining Methods and Conditions
```python
low_battery_count = 0

for robot in robots:
    robot.report()
    if robot.battery_level < 50:
        low_battery_count += 1

print("Low battery robots:", low_battery_count)
```

### Example 4: Different Class (Guest)
```python
class Guest:
    def __init__(self, name):
        self.name = name

    def greet(self):
        print(f"Hello, I'm {self.name}!")

guests = [
    Guest("Alice"),
    Guest("Bob"),
    Guest("Charlie")
]

for guest in guests:
    guest.greet()
```

## 6. Common Mistakes / What Not to Do
- **Using range(len()) unnecessarily**: `for i in range(len(robots)): robots[i].diagnose()` is more complex than needed. Use `for robot in robots: robot.diagnose()`.
- **Calling method on wrong thing**: `diagnose(robots[i])` assumes a standalone function, not an object method. Use `robots[i].diagnose()`.
- **Treating loop variable as index**: `for i in robots:` treats each item as an index when it's actually the object. Use `for robot in robots:`.
- **Printing inside loop vs. after loop**: Printing counts inside the loop prints every time; move final prints outside the loop for summary output.

## 7. Open-Note Review
- Loop variable is the full object, not an index or value
- Use `for object in objects:` to iterate over object lists
- Access attributes with dot notation: `object.attribute`
- Call methods with dot notation: `object.method()`
- Can combine method calls and attribute checks in same loop
- Avoid `range(len())` pattern when direct iteration works

## 8. Final Takeaway
When looping over a list of objects, the loop variable is the full object—use dot notation to access its attributes and methods directly, combining operations as needed within the loop.

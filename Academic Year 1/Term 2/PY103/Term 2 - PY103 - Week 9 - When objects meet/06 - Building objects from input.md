# Building Objects from Input

## 1. Lesson Focus
Creating multiple objects from user input using a loop, storing them in a list, and then accessing their attributes.

## 2. Core Concepts
**Input in Loop**: Using `input()` inside a for loop to collect data from the user for each object.

**Object Creation in Loop**: Calling the class constructor each time through the loop to create new objects.

**Append to List**: Using `list.append(object)` inside the loop to store each newly created object.

**Loop Count Controls Objects**: The number of loop iterations determines how many objects are created (e.g., `range(3)` creates 3 objects).

## 3. Key Details to Remember
- Use `for i in range(n):` to control how many objects to create
- Call `input()` inside the loop to get data for each object
- Convert string input to appropriate types (e.g., `int(input())` for numbers)
- Create object after collecting input, then immediately append to list
- Append must be inside the loop, not outside
- After loop, iterate over list to access stored objects

## 4. Implementation Pattern

**Input → Create → Append Pattern**:
```python
objects = []

for i in range(n):
    data1 = input("Prompt: ")
    data2 = int(input("Prompt: "))

    obj = ClassName(data1, data2)
    objects.append(obj)

# Use objects
for obj in objects:
    print(obj.attribute)
```

## 5. Examples

### Example 1: Registering Attendees
```python
class Attendee:
    def __init__(self, name, age):
        self.name = name
        self.age = age

attendees = []

for i in range(3):
    name = input("Enter attendee name: ")
    age = int(input("Enter attendee age: "))

    attendee = Attendee(name, age)
    attendees.append(attendee)

print("We registered", len(attendees), "attendees.")

for person in attendees:
    print(person.name, "-", person.age)
```

### Example 2: Pattern Breakdown
```python
# Step 1: Define class
class Attendee:
    def __init__(self, name, age):
        self.name = name
        self.age = age

# Step 2: Create empty list
attendees = []

# Step 3: Loop to collect input and create objects
for i in range(3):
    # Collect input
    name = input("Enter attendee name: ")
    age = int(input("Enter attendee age: "))

    # Create object
    attendee = Attendee(name, age)

    # Store in list (MUST be inside loop)
    attendees.append(attendee)

# Step 4: Use the stored objects
for person in attendees:
    print(person.name, "-", person.age)
```

## 6. Common Mistakes / What Not to Do
- **Appending outside loop**: `attendees.append(attendee)` outside the loop only stores the last object. Append must be inside the loop after each object creation.
- **Forgetting type conversion**: `input()` returns strings. Use `int()` or `float()` for numeric data.
- **Creating list inside loop**: Creating the list inside the loop resets it each time. Create list before the loop.
- **Wrong loop placement**: Putting append before object creation or in wrong location. Order: input → create → append.

## 7. Open-Note Review
- Use `for i in range(n):` to control object count
- Call `input()` inside loop for each object's data
- Convert input to correct type (e.g., `int()`)
- Create object after collecting input
- Append object to list immediately after creation
- Append must be inside the loop
- Iterate over list after loop to access objects

## 8. Final Takeaway
Create multiple objects from user input by looping, collecting input, calling the constructor, and appending each new object to a list—the loop count determines how many objects are created.

# Challenge I: RobotCourier and Package System

## 1. Lesson Focus
A hands-on challenge to model a real-world scenario with two collaborating classes: a `RobotCourier` that delivers `Package` objects across town, demonstrating object-to-object collaboration and state changes.

---

## 2. Core Concepts

### Object-to-Object Collaboration
Objects can call methods on other objects, passing them as arguments to methods.

```python
robot.deliver(package, km)  # robot calls package.show_destination()
```

### State Changes Across Method Calls
Methods can modify attributes, and subsequent calls see the updated state.

```python
self.distance_left = self.distance_left - km
```

### Multiple Classes Working Together
Different classes model different real-world entities, each with their own attributes and methods.

---

## 3. Key Details to Remember

- **Method parameters:** Methods can take objects as arguments, not just simple values
- **Collaboration:** One object's method can call another object's methods
- **State persistence:** Changes to attributes persist across method calls
- **Multiple instances:** Can create multiple objects from the same class with different states
- **`self` vs object variables:** Inside methods, use `self`; when calling methods on other objects, use the object variable name

---

## 4. Examples

### RobotCourier Class
```python
class RobotCourier:
    def travel(self, km):
        print("Traveling", km, "km")
        self.distance_left = self.distance_left - km
        print(self.distance_left, "km remaining!")

    def deliver(self, package, km):
        package.show_destination()
        self.travel(km)
        package.mark_delivered()
```

### Package Class
```python
class Package:
    def show_destination(self):
        print("Deliver to", self.destination)

    def mark_delivered(self):
        self.delivered = True
        print("Package delivered!")
```

### Full Working Example
```python
class RobotCourier:
    def travel(self, km):
        print("Traveling", km, "km")
        self.distance_left = self.distance_left - km
        print(self.distance_left, "km remaining!")

    def deliver(self, package, km):
        package.show_destination()
        self.travel(km)
        package.mark_delivered()

class Package:
    def show_destination(self):
        print("Deliver to", self.destination)

    def mark_delivered(self):
        self.delivered = True
        print("Package delivered!")

# Create objects
robot = RobotCourier()
robot.distance_left = 15

package = Package()
package.destination = "Downtown"
package.delivered = False

# Deliver
robot.deliver(package, 5)
# Output:
# Deliver to Downtown
# Traveling 5 km
# 10 km remaining!
# Package delivered!

robot.deliver(package, 3)
# Output:
# Deliver to Downtown
# Traveling 3 km
# 7 km remaining!
# Package delivered!
```

### Multiple Packages
```python
package2 = Package()
package2.destination = "Airport"

robot.deliver(package2, 4)
# robot.distance_left becomes 3
# package2.delivered becomes True
```

---

## 5. Common Mistakes / What Not to Do

| Mistake | Why It Fails |
|---------|--------------|
| Forgetting method parameters | `robot.travel()` needs `km` argument: `robot.travel(5)` |
| Using wrong object name in methods | Inside `mark_delivered`, use `self.delivered`, not `package.delivered` |
| Not setting initial attributes | Must set attributes after creating objects: `robot.distance_left = 15` |
| Confusing `self` with other objects | `self` refers to the object the method is called on, not other objects |

---

## 6. Open-Note Review

**Collaboration Pattern**
```python
def deliver(self, package, km):
    package.show_destination()  # Call other object's method
    self.travel(km)            # Call own method
    package.mark_delivered()    # Update other object's state
```

**State Change Pattern**
```python
self.distance_left = self.distance_left - km  # Update own attribute
self.delivered = True                         # Set boolean attribute
```

**Key Insight**
> Each object has its own memory (attributes) and skills (methods). Programs are objects talking to each other.

---

## 7. Final Takeaway

OOP programs are built from multiple classes where objects collaborate by calling each other's methods. One object can accept another object as an argument and interact with it. Each object maintains its own state, and method calls modify that state over time. This collaboration between objects is the foundation of object-oriented design.

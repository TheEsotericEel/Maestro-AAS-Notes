# Methods and the Role of Self

## 1. Lesson Focus
Introduces **methods** (functions defined inside classes) and explains the role of **`self`** — the first parameter that automatically receives the object calling the method.

---

## 2. Core Concepts

### Method
**Definition:** A function defined inside a class that represents behavior for objects of that class.

```python
class Dog:
    def bark(self):
        print("Woof!")
```

### `self` Parameter
**Definition:** The first parameter in an instance method that automatically receives the object calling the method.

**Meaning:** `self` = "this specific object, the one on the left of the dot"

**How it works:**
```python
buddy = Dog()
buddy.bark()      # Python secretly rewrites as: Dog.bark(buddy)
```
Inside `bark`, `self` is `buddy`.

### Rule of Thumb
```
object.method()  →  inside the method, self is that object
```

---

## 3. Key Details to Remember

- **Method syntax:** Always define instance methods as `def method_name(self):`
- **`self` is required:** Instance methods must have `self` as the first parameter
- **Python passes automatically:** When you call `object.method()`, Python passes the object into `self` for you
- **`self` naming convention:** Python always uses `self` for clarity, though other names would technically work

---

## 4. Examples

### Dog Class with Bark Method
```python
class Dog:
    def bark(self):
        print("Woof!")

buddy = Dog()
buddy.bark()    # Output: Woof!
```

### Multiple Objects Calling the Same Method
```python
class Dog:
    def bark(self):
        print("Woof!")

buddy = Dog()
buddy.bark()    # self is buddy

rex = Dog()
rex.bark()      # self is rex
```

### LightSwitch Class
```python
class LightSwitch:
    def flip(self):
        """Make a click sound when the switch is flipped."""
        print("Click!")

living_room = LightSwitch()
living_room.flip()   # Output: Click!
# Inside flip, self is living_room
```

### Cat Class with Meow Method
```python
class Cat:
    def meow(self):
        print("Meow!")

whiskers = Cat()
whiskers.meow()   # Output: Meow!
# Inside meow, self is whiskers
```

---

## 5. Common Mistakes / What Not to Do

| Mistake | Why It Fails |
|---------|--------------|
| `def meow():` (no `self`) | Missing first parameter — won't work as an instance method |
| `def meow(cat):` | Technically works but violates Python convention — always use `self` |
| Calling a method that doesn't exist | `AttributeError: 'Dog' object has no attribute 'bark'` |
| Indenting main code inside the class | Main code should be at left margin, not inside the class |

---

## 6. Open-Note Review

**Method Definition Pattern**
```python
class ClassName:
    def method_name(self):
        # method body
```

**Calling Methods**
```python
object = ClassName()
object.method_name()   # Python passes object into self
```

**Quick Reference**

| Call | Inside the method, `self` is |
|------|------------------------------|
| `buddy.bark()` | `buddy` |
| `rex.bark()` | `rex` |
| `living_room.flip()` | `living_room` |
| `whiskers.meow()` | `whiskers` |

---

## 7. Final Takeaway

A **method** is a function inside a class that defines behavior. The **`self`** parameter is the first parameter of any instance method and automatically receives the object calling the method. When you write `object.method()`, Python secretly passes that object into `self` — so `self` always means "this specific object, the one on the left of the dot."

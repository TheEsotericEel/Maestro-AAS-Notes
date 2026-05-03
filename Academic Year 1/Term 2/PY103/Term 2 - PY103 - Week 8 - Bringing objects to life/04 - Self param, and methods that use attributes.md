# Self Param, and Methods That Use Attributes

## 1. Lesson Focus
Shows how methods use `self.attribute` to access the attributes of the specific object calling the method, and demonstrates that changing attributes later changes method behavior without changing the method code.

---

## 2. Core Concepts

### `self.attribute` Access
**Syntax:** `self.attribute_name`

**Meaning:** Access the attribute of the specific object that called the method.

```python
class Dog:
    def speak(self):
        print("My name is", self.name)
```

When `fido.speak()` runs, `self` is `fido`, so `self.name` is `fido.name`.

### Same Method, Different Objects
The same method can produce different output when called on different objects because `self` points to different instances.

```python
fido.speak()  # self is fido
luna.speak()  # self is luna
```

### Methods Use Current Attribute Values
Methods don't "remember" old values — they always use the **current** value of the attributes on `self` at the time of the call.

---

## 3. Key Details to Remember

- **`self.attribute`** reads the attribute of the specific object that called the method
- **Same method, different objects** → different output because `self` points to different instances
- **Changing attributes later** changes what methods print, without changing the method code
- **Methods always use current values** — they don't cache or remember old attribute values

---

## 4. Examples

### Dog Class with speak() Method
```python
class Dog:
    def speak(self):
        print("My name is", self.name)

fido = Dog()
fido.name = "Fido"

luna = Dog()
luna.name = "Luna"

fido.speak()  # Output: My name is Fido
luna.speak()  # Output: My name is Luna
```

### Changing Attribute Changes Method Behavior
```python
class Dog:
    def speak(self):
        print("My name is", self.name)

luna = Dog()
luna.name = "Luna"
luna.speak()      # Output: My name is Luna

luna.name = "MoonDog"  # Change attribute
luna.speak()      # Output: My name is MoonDog
```

### LightSwitch Example
```python
class LightSwitch:
    def show_state(self):
        print("The light is", self.state)

kitchen = LightSwitch()
kitchen.state = "OFF"

living_room = LightSwitch()
living_room.state = "ON"

kitchen.show_state()    # Output: The light is OFF
living_room.show_state() # Output: The light is ON
```

### Changing State Changes Method Output
```python
bedroom = LightSwitch()
bedroom.state = "ON"
bedroom.show_state()  # Output: The light is ON

bedroom.state = "OFF"  # Change attribute
bedroom.show_state()  # Output: The light is OFF
```

### Multiple Objects with Attribute Changes
```python
class Dog:
    def speak(self):
        print("My name is", self.name)

fido = Dog()
fido.name = "Fido"

rex = Dog()
rex.name = "Rex"

fido.name = "Sir Fido"  # Change fido's name

fido.speak()  # Output: My name is Sir Fido
rex.speak()   # Output: My name is Rex
```

---

## 5. Common Mistakes / What Not to Do

| Mistake | Why It Fails |
|---------|--------------|
| Assuming methods remember old attribute values | Methods always use the current value at call time |
| Thinking `self` refers to the class | `self` is the specific object, not the class |
| Forgetting that changing an attribute changes method output | Same method + new attribute value = new behavior |

---

## 6. Open-Note Review

**Accessing Attributes in Methods**
```python
def method(self):
    print(self.attribute_name)
```

**Key Rule**
> Same method, different objects → different output because `self` points to different instances.

**Attribute Changes**
> Changing an attribute later changes what the method prints, without changing the method code.

---

## 7. Final Takeaway

Methods use `self.attribute` to access the attributes of the specific object calling the method. Because `self` is the object on the left of the dot, the same method can behave differently for different objects. Methods always use the **current** attribute values at call time — changing an attribute changes the method's behavior without modifying the method code.

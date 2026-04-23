> Course: PY103
> Lesson: Creating your first class

# Creating Your First Class

## 1. Lesson Focus
Learning the syntax to define a basic Python class (the blueprint), create an instance or object from it, and dynamically attach attributes to that created instance.

---

## 2. Core Concepts: The Three Steps of Class Creation

To successfully implement a custom object-oriented structure in Python, you must sequentially execute three actions:

### 1. Define the Blueprint (The Class)
A class block establishes the template. A minimal class doesn't need data yet; it just needs a name and the `pass` keyword to act as a placeholder.
* **Example:** `class Pet:`

### 2. Create the Object (The Instance)
Using the class name followed by parentheses `()` tells Python to allocate memory and spawn a fresh, usable object from the defined blueprint. 
* **Example:** `fido = Pet()`

### 3. Add Details (The Attributes)
Once the instance exists in memory, you can dynamically assign data to it using dot notation (`object.property`). 
* **Example:** `fido.name = "Fido"`

---

## 3. The Code Pattern in Action

Here is an end-to-end example establishing a `Planet` class and filling out an instance:

```python
# 1. Blueprint: Define the class
class Planet:
    pass

# 2. Create Object: Spawn an instance in memory
earth = Planet()

# 3. Add Details: Attach attributes to the object
earth.name = "Earth"
earth.diameter_km = 12742

# Access the attributes using dot notation
print(earth.name)         # Output: Earth
print(earth.diameter_km)  # Output: 12742
```

---

## 4. Inspecting Objects

If you are unsure whether an object was successfully created from your custom class, Python provides a built-in helper function to check its underlying blueprint.

```python
class Pet:
    pass

fido = Pet()

# 'type()' inspects an object and reveals its class
print(type(fido))  
# Console Output: <class '__main__.Pet'>
```

---

## 5. Common Mistakes & Logic Traps

### Misidentifying the "Creation" Line
It is a common pitfall to assume the `class` keyword builds an object.
* ❌ `class Pet:` does **not** create a real pet. It only writes the blueprint.
* ✅ `fido = Pet()` is the exact moment the object is manifested into memory.

### Failing to Attach Data to the Object
When trying to give your object attributes, you must explicitly use the object's name and dot notation.
* ❌ **Standalone Variable:** `diameter_km = 12742` (This is completely disconnected from the Earth object).
* ✅ **Attached Attribute:** `earth.diameter_km = 12742` (This safely stores the data *inside* the Earth object).

---

## 6. Open-Note Review

- `class Name:` establishes the blueprint framework.
- `instance = Name()` builds the actual object.
- `instance.attribute = value` attaches data directly to the object.
- The `type(instance)` command prints out the class blueprint of any Python object.

**Quick self-test**
> In the code `earth = Planet()`, which line creates the actual object?
> → `earth = Planet()`
> If you omit the dot notation and write `name = "Earth"`, is the data attached to the planet?
> → No, it is just a standalone variable hovering outside the object.

---

## 7. Final Takeaway
Building out custom Python objects relies on a strict order of operations: **Blueprint** (`class`), then **Object** (`instance = Class()`), and then **Details** (`instance.data = data`).

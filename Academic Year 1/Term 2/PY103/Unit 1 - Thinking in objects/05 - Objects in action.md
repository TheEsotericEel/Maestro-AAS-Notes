> Course: PY103
> Lesson: Objects in action

# Objects in Action

## 1. Lesson Focus
Understanding the fundamental object-oriented sequence: interacting with objects through a three-step cycle of **Thing** (Object) → **Action** (Method) → **Result** (Data).

---

## 2. Core Concepts

### Object (The Thing)
**Definition:** A specific, ready-to-use instance you create.
* Analogy: Buying a dice-rolling machine and putting it on your desk. 
* Creating the object does not immediately produce data; it just prepares the object for use.
* Example: `rng = random.Random()` creates the object.

### Method (The Action)
**Definition:** An action or behavior that belongs specifically to that object.
* Analogy: Pressing the button on your dice-rolling machine.
* Methods often require arguments (inputs) to know exactly how to behave.
* Example: `.randint(1, 100)` or `.random()`.

### Data (The Result)
**Definition:** The final value returned after the method finishes executing.
* Analogy: The number the machine spits out.
* This is what you actually store in a variable or print.
* Example: The random integer, like `84`, stored in `value`.

---

## 3. The Core Sequence: Thing → Action → Result

The core dynamic of Object-Oriented Programming works exactly in this order:

| Step | Concept | Example Code |
|------|---------|--------------|
| **1. Create** | The Object (Thing) | `rng = random.Random()` |
| **2. Call**   | The Method (Action) | `rng.random()` |
| **3. Store**  | The Data (Result) | `value = ...` |

Combined into one sequence:
```python
# 1. Thing      2. Action     3. Result
rng        .    random()  ->  returns e.g. 0.575
```

---

## 4. Example: The Sequence in Code

```python
import random

# 1. Prepare the object (The Thing)
rng = random.Random()

# 2. Call the method (The Action) to generate the data (The Result)
first = rng.random()
second = rng.random()

# 3. Print the resulting data
print(first)   # Output: 0.575350220570524
print(second)  # Output: 0.7438121436899181
```

---

## 5. What Not to Do / Common Misunderstandings

**Don't confuse the data variable with the object.**
Consider this line: `value = rng.randint(1, 100)`
* `value` is **not** the object. It's just a regular variable holding the resulting data.
* `rng` is the actual object instance.
* `(1, 100)` are the arguments (inputs) going into the method, not the data coming out.

---

## 6. Open-Note Review

- `random.Random()` creates an instance of the Random class. It does not instantly produce a number.
- `rng.randint()` performs an action using that specific object.
- The returned data must be assigned to a variable if you want to save the result.

**Quick self-test**
> In `value = rng.random()`, what does `rng` represent?
> → The object (instance) created from `random.Random()`.
> What about `value`? 
> → The data returned by calling the method.

---

## 7. Final Takeaway
The entire foundation of using objects boils down to: you build an **Object** (the thing), you call its **Methods** (the actions), and it hands you back **Data** (the results).

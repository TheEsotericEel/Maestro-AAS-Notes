# What Is OOP and Why Do We Need It?

## 1. Lesson Focus
Introduces Object-Oriented Programming (OOP) as a programming paradigm — a way of organizing programs around objects that bundle data and behavior — and distinguishes it from procedural (step-by-step) programming.

---

## 2. Core Concepts

### Programming Paradigm
**Definition:** A general style or approach for organizing how we write programs.

Common paradigms:
| Paradigm | Core Idea |
|----------|-----------|
| **Procedural** | Programs as a list of steps executed top to bottom |
| **Object-Oriented (OOP)** | Programs built from objects that have data + behavior |
| **Functional** | Programs as data flowing through functions |

### Object-Oriented Programming (OOP)
**Definition:** A programming paradigm where programs are built from **objects** — things that bundle:
- **Data** (attributes) — what the object *is* or *has*
- **Behavior** (methods) — what the object *can do*

### Procedural vs. OOP
| Procedural | Object-Oriented |
|-----------|----------------|
| One long list of steps | Collection of interacting objects |
| "Do step 1, step 2, step 3…" | "Objects know what they can do" |
| Like a recipe | Like real-world things working together |

---

## 3. Key Details to Remember

- **Python is object-oriented** — even basic built-in types are objects:
  - `"hello"` → a **string object** (data = characters; behavior = `.upper()`, `.split()`, etc.)
  - `[1, 2, 3]` → a **list object** (data = items; behavior = `.append()`, `.remove()`, etc.)
  - `42` → even integers are objects in Python
- You've already been using OOP without naming it whenever you used strings and lists.

---

## 4. What an Object Looks Like (Conceptually)

Every object has two parts:

```
Object: BankAccount
  Data:      balance = 500, owner = "Alice"
  Behavior:  deposit(), withdraw(), get_balance()
```

```
Object: Cat
  Data:      color = "orange", voice = "meow"
  Behavior:  eat(), sleep(), meow()
```

The object bundles both together — you don't separate the data from the actions that operate on it.

---

## 5. Open-Note Review

**Key Terms**
- **Programming paradigm:** A general style for organizing programs
- **Procedural:** Step-by-step list of instructions
- **OOP:** Programs built from objects with data + behavior
- **Object:** A bundle of data (attributes) + behavior (methods)

**Quick Checks**
- What is a paradigm? → A style/approach for organizing programs
- What does OOP stand for? → Object-Oriented Programming
- What two things does every object bundle? → Data + behavior
- Are Python strings objects? → Yes — they have data (characters) and behavior (methods like `.upper()`)

**The Core OOP Idea**
> Instead of one long list of steps, OOP builds programs from objects — each object knows what it *has* (data) and what it *can do* (behavior).

---

## 6. Final Takeaway

OOP is a programming paradigm that organizes programs around **objects** — things that bundle **data** (attributes) and **behavior** (methods). Python is built around this idea: strings, lists, and even numbers are all objects. OOP shifts thinking from "what steps do I run?" to "what objects exist and what can they do?"

# Lesson 11: Talking to Your Program (Input)

## 🎯 End Goal
To create interactive programs that pause execution to accept data from the user, and to safely convert that raw text into usable data types.

## 🧠 Core Concepts

### 1. Blocking I/O (The Pause)
The `input()` function is a **Blocking Operation**.
*   **Behavior**: When the computer hits this line of code, it **stops** everything. It enters a "Wait State."
*   **Resume**: It will not execute the next line of code until the user types something and presses `ENTER`.

### 2. The Return Value (Strings Only)
`input()` captures keys pressed on a keyboard. Therefore, the result is **ALWAYS** a String.
*   User types: `42`
*   Program receives: `"42"`
*   **Implication**: You cannot do math on input directly. You must cast it.

### 3. User Experience (UX)
The text inside `input("...")` is called the **Prompt**.
*   **Bad UX**: `input("Name:")` -> Cursor sits continuously next to the colon. hard to read.
*   **Good UX**: `input("Name: ")` -> The trailing space gives the user visual breathing room.

## 📝 Standards and Patterns

### The "Prompt-Cast-Assign" Pattern
For numbers, we wrap the input call in a caster.

```python
# Broken
age = input("Age: ")
print(age + 1) # Error! Cannot add Int to String.

# Fixed
age = int(input("Age: "))
print(age + 1) # Logic works.
```

### Data Hygiene (`.strip()`)
Users make mistakes. They often type spaces by accident (`" Alice "`).
Use `.strip()` to remove leading/trailing whitespace.

```python
name = input("Name: ").strip()
```

## ⚠️ Traps and Pitfalls

| Mistake | Code | Why it fails |
| :--- | :--- | :--- |
| **Silent Prompt** | `input()` | The cursor blinks on a blank line. User thinks the program crashed. **Always** provide a prompt string. |
| **The Math Crash** | `input("Age: ") * 2` | If user enters 10, result is `"1010"`, not `20`. |
| **Blind Casting** | `int(input("Age: "))` | If user types "Twenty", the program crashes with `ValueError`. (We will fix this in Week 2 with Error Handling). |

## 🛠️ Step-by-Step Execution
Assume user types "10" and hits Enter.

```python
value = int(input("Enter number: "))
```

1.  **Print**: "Enter number: " displays on screen.
2.  **Wait**: Program pauses.
3.  **User**: Types `1`, `0`, `[ENTER]`.
4.  **Return**: `input` resolves to string `"10"`.
5.  **Cast**: `int("10")` converts it to integer `10`.
6.  **Assign**: Variable `value` stores `10`.

## 🔍 Truth Lines
```python
# User enters: 5
x = input()
print(type(x)) # <class 'str'>

# User enters: 5
y = int(input())
print(type(y)) # <class 'int'>
```

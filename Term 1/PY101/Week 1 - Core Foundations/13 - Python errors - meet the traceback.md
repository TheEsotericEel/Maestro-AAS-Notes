# Lesson 13: Python Errors - Meet the Traceback

## 🎯 End Goal
To transform your relationship with errors. Instead of fearing "Red Text," you will learn to read the **Traceback** as a precise diagnostic report that tells you exactly what went wrong and where.

## 🧠 Core Concepts

### 1. The Traceback (The Crash Report)
When Python encounters code it cannot understand or execute, it raises an **Exception** and prints a Traceback.
*   **Structure**: It is a stack of events, printed from oldest (top) to newest (bottom).
*   **Reading Strategy**: **ALWAYS READ THE BOTTOM LINE FIRST.**

### 2. The Three-Step Fix
1.  **What**: Read the Error Type and Message (Bottom line).
2.  **Where**: Read the File and Line Number (Second to last line).
3.  **Why**: Look at the code *above* that line to find the cause.

## 🛠️ Anatomy of an Error

```text
Traceback (most recent call last):
  File "game.py", line 42, in <module>    <-- WHERE
    print(score + " points")              <-- OFFENDING CODE
TypeError: unsupported operand type(s)    <-- WHAT
for +: 'int' and 'str'
```
*   **The "What"**: `TypeError`. You tried to add an Integer and a String.
*   **The "Where"**: Line 42 of `game.py`.

## ⚠️ The Big Five Errors

| Error Type | Meaning | Common Cause | Fix |
| :--- | :--- | :--- | :--- |
| **SyntaxError** | "I don't understand this grammar." | Missing `)`, `]`, `"`, or `:`. | Check the line **ABOVE** the reported line. |
| **IndentationError** | "Your spacing is messy." | Mixing tabs and spaces. | Consistency. Use 4 spaces. |
| **NameError** | "I don't know that word." | Typo in variable name. Using variables before defining them. | Check spelling. Check case (`Score` vs `score`). |
| **TypeError** | "Square peg, round hole." | Math on non-numbers. `input() + 5`. | Cast your data: `int(input())`. |
| **ValueError** | "Right type, wrong content." | `int("Hello")`. | Validate input before casting. |

## 📝 Debugging Strategy: The "Line Before" Rule
for `SyntaxError`, Python often points to the line *after* the mistake.
```python
print("Hello"   <-- Missing closing paren
print("World")  <-- Error points here!
```
*   **Why**: Python didn't realize the statement was broken until it hit the *next* command.
*   **Rule**: If line X looks perfect, check line X-1.

## ⚡ Associations
*   **Traceback** → Read Bottom-Up.
*   **SyntaxError** → Check Line Above.
*   **NameError** → Check Typos.
*   **TypeError** → Check Casting.

## 🔍 Truth Lines
```text
print(unknown_var) -> NameError
print("5" + 10) -> TypeError
int("Five") -> ValueError
print("Hi") -> SyntaxError (Missing quote)
```

# Lesson 03: Introduction to Variables

## 🎯 End Goal
To separate **data** from **code** using variables. You will learn to store, retrieve, and update information in the computer's memory using clear, professional naming conventions.

## 🧠 Core Concepts

### 1. The Variable (The Label)
A variable is a **name** attached to a **value** in the computer's memory.
*   **Analogy**: It is not a box that holds the value. It is a specific **tag** or **reference** tied to a piece of data.
*   **Why**: We need to store results (like a score or a username) to use them later.

### 2. The Assignment Operator (`=`)
In Python, the equals sign `=` does **not** check if two things are equal. It is an **command**.
*   **Command**: "Take the value on the RIGHT and store it in the name on the LEFT."
*   **Rule**: `Target = Value`. You cannot write `10 = score`. The name must always be on the left.

### 3. Dynamic Typing
Python is "Dynamically Typed." This means a variable can hold an Integer at one moment and a String at the next.
*   *Note*: While possible, changing types wildly is often bad practice because it confuses other programmers (and you).

## 📝 The Rules of Naming (PEP 8)
We follow the **Snake Case** convention for variables in Python.

| Type | Rule | Example | Why? |
| :--- | :--- | :--- | :--- |
| **Valid** | Lowercase words separated by underscores. | `player_score`, `user_id` | Maximum readability. |
| **Invalid** | Starting with a number. | `1st_place` | Syntax Error. |
| **Invalid** | Using spaces. | `user name` | Syntax Error (Python sees two words). |
| **Bad Style** | CamelCase (used in Java/JS). | `playerScore` | Not Pythonic. |
| **Bad Style** | Single letters. | `x`, `n` | What does `n` mean? Use `count`. |

## 🔄 The Assignment Flow
Variables are processed in a specific order: **Right-to-Left**.

```python
score = 10 + 5
```
1.  **Evaluate**: The computer looks at the right side (`10 + 5`).
2.  **Calculate**: It calculates the result (`15`).
3.  **Assign**: It attaches the name `score` to the value `15`.

### The "Update" Pattern
This is the most confusing concept for beginners because it looks mathematically impossible.

```python
count = 10
count = count + 1
```

1.  **Right side first**: Look at `count + 1`.
2.  **Retrieve**: What is `count` right now? It is `10`. So, `10 + 1` = `11`.
3.  **Assign**: Store `11` back into the name `count`.
4.  **Result**: `count` is now `11`.

## ⚡ Associations
*   **`=`**: Assignment (Action). reads as "gets set to".
*   **`==`**: Equality Check (Question). We will learn this later.
*   **`snake_case`**: The "uniform" of a Python variable.

## ⚠️ Traps and Pitfalls

| Mistake | Code | Error Type | Explanation |
| :--- | :--- | :--- | :--- |
| **The Math Fallacy** | `x = x + 1` | `(None)` | Beginners think this is valid math ($x = x + 1 \implies 0 = 1$). In code, it is an **update**. |
| **Reversed Assignment** | `10 = score` | `SyntaxError` | "Cannot assign to literal." The destination must be on the left. |
| **Undefined Variable** | `print(total)` | `NameError` | You tried to read a variable before you created it. |
| **Case Sensitivity** | `Score = 10`<br>`print(score)` | `NameError` | `Score` and `score` are two different people. |

## 🔍 Truth Table: Valid Names

| Name | Status | Comment |
| :--- | :--- | :--- |
| `total_cost` | ✅ Valid | Perfect. |
| `TotalCost` | ⚠️ Valid | But bad style (Java style). |
| `total cost` | ❌ Invalid | Spaces are not allowed. |
| `class` | ❌ Invalid | "class" is a reserved word in Python. |
| `cost_in_$` | ❌ Invalid | Special characters like `$` are not allowed. |

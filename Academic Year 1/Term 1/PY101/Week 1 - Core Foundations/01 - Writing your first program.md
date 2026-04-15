# Lesson 01: Writing Your First Program

## 🎯 End Goal
To successfully execute your first Python instruction and understand the fundamental mechanism of **function calls** and **string literals**.

## 🧠 Core Concepts

### 1. The `print()` Function
In Python, `print` is not a command to sending a document to a physical printer. It is a **function** that sends data to the standard output (your terminal screen).

*   **What**: A built-in utility that displays information.
*   **Why**: Programs must communicate with the user. Without output, a program is a black box—you have no idea if it succeeded or failed.
*   **How**: You "call" the function by writing its name followed by parentheses `()`.

### 2. Strings (Text Data)
Computer code is a mix of **instructions** (verbs) and **data** (nouns).
*   **Instruction**: `print` (Do this!)
*   **Data**: `"Hello"` (Use this!)

To tell Python that "Hello" is text data and not an instruction, we enclose it in quotes. This is called a **String Literal**.

### 3. Case Sensitivity
Python is case-sensitive. `print` is a valid function. `Print`, `PRINT`, and `PrInT` do not exist.

## 📝 The "Hello, World!" Tradition
It is a rite of passage for every programmer to write a program that simply displays "Hello, World!". This tradition dates back to 1978, popularized by Brian Kernighan and Dennis Ritchie in their book *The C Programming Language*.

### The Code
```python
print("Hello, World!")
```

### Anatomy of a Function Call
```text
  Function Name     Open Parenthesis      String Literal      Close Parenthesis
      ↓                    ↓                    ↓                    ↓
    print                  (             "Hello, World!"             )
```

1.  **`print`**: The identifier looking for the function definition.
2.  **`(`**: The trigger. It tells Python, "Do it now!"
3.  **`"..."`**: The argument. This is the input we are passing *into* the function.
4.  **`)`**: The terminator. It marks the end of the input.

## 🔄 The Execution Flow
When you run a Python file, the interpreter reads it **top to bottom, line by line**.

```python
print("Line 1")
print("Line 2")
print("Line 3")
```

**Output**:
```text
Line 1
Line 2
Line 3
```
It will never print Line 3 before Line 1. This deterministic behavior is the foundation of algorithmic logic.

## ⚡ Associations
*   **Green Text (in most editors)**: This is a String (Data).
*   **Parentheses `()`**: This is a Function Call (Action).
*   **`#`**: A Comment. Python ignores everything after this symbol on the same line. Use it for notes.

## ⚠️ Traps and Pitfalls

| Mistake | Code | Error Type | Why? |
| :--- | :--- | :--- | :--- |
| **Capitalization** | `Print("Hello")` | `NameError` | Python looks for a function named `Print` and cannot find it. |
| **Missing Quotes** | `print(Hello)` | `NameError` | Python thinks `Hello` is a variable name, tries to find its value, and fails. |
| **Missing Parentheses** | `print "Hello"` | `SyntaxError` | In Python 3, parentheses are mandatory. This was valid only in Python 2 (ancient history). |
| **Mismatched Quotes** | `print("Hello')` | `SyntaxError` | You opened with double quotes but tried to close with a single quote. Pick one and stick to it. |

## 🔍 Professional Standards
*   **Double vs. Single Quotes**: Python accepts both `"Hello"` and `'Hello'`.
    *   *Standard*: Use **double quotes** `"` for actual text (sentences, words).
    *   *Standard*: Use **single quotes** `'` for technical identifiers (keys, codes) or if the string contains a double quote inside it (e.g., `print('He said "Hello"')`).
*   **Whitespace**: `print( "Hello" )` works, but `print("Hello")` is preferred. Avoid unnecessary spaces inside the parentheses.
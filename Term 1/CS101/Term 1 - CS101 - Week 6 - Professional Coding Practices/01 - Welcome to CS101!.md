# Welcome to CS101: Professional Coding Practices

## 1. Introduction
Welcome to Computer Science 101. Unlike introductory programming courses (like PY101) which focus on *syntax* and *getting it to work*, CS101 focuses on **Software Engineering**: the discipline of designing, building, and maintaining software systems that are reliable, efficient, and readable.

In this module, we shift our focus from "writing code" to "crafting software".

> **The Professional Standard**: "Code is read much more often than it is written." — *Guido van Rossum* (Creator of Python)

## 2. Core Concept: Maintainability
In academic and professional software engineering, **Maintainability** is the ease with which a software system or component can be modified to correct faults, improve performance, or adapt to a changed environment.

### Why It Matters
*   **Economic Reality**: The majority of the cost of software lies in its maintenance phase, not its initial development.
*   **Cognitive Load**: Complex, messy code increases the cognitive load required to understand it, leading to bugs.
*   **Collaboration**: Professional software is built by teams. Your code acts as communication to your future self and your colleagues.

### The Mechanism
We achieve maintainability through specific practices:
1.  **Readability**: Adhering to style guides (PEP 8) and writing self-documenting code.
2.  **Modularity**: Breaking problems into small, single-purpose functions (Single Responsibility Principle).
3.  **Robustness**: Anticipating failure states and handling them gracefully (Error Handling).

## 3. Notable Figures
*   **Robert C. Martin (Uncle Bob)**: Author of *Clean Code*, advocating for code that reads like well-written prose.
*   **Steve McConnell**: Author of *Code Complete*, highlighting the importance of construction practices in software quality.
*   **Guido van Rossum**: Emphasized readability as a core design philosophy of Python.

## 4. The Shift in Perspective
We are moving from a "Scripting Mindset" to an "Engineering Mindset".

| Feature | Scripting Mindset (PY101) | Engineering Mindset (CS101) |
| :--- | :--- | :--- |
| **Goal** | Make it run. | Make it last. |
| **Audience** | The Computer. | Humans (and the Computer). |
| **Structure** | Linear, top-to-bottom. | Modular, functional, reusable. |
| **Errors** | Fix them as they appear. | Anticipate and handle them. |
| **Testing** | Run it and see. | Automated, systematic verification. |

## 5. Practical Example: The Difference

### The "Novice" Approach
This code "works" but is obscure, hard to debug, and impossible to maintain.

```python
# Bad Code
x = input("Enter: ")
y = 0
for i in x:
    if i == 'a':
        y += 1
print(y)
```

### The "Professional" Approach
This code performs the same task but is explicit, reusable, and documents its intent.

```python
def count_vowels(text_input: str, target_char: str = 'a') -> int:
    """
    Counts the occurrences of a specific character in a string.
    
    Args:
        text_input (str): The string to search.
        target_char (str): The character to count. Defaults to 'a'.
        
    Returns:
        int: The count of target_char in text_input.
    """
    if not text_input:
        return 0
        
    count = 0
    for char in text_input:
        if char == target_char:
            count += 1
    return count

# Usage
user_input = input("Enter text to analyze: ")
a_count = count_vowels(user_input, 'a')
print(f"Found {a_count} occurrences of 'a'.")
```

## 6. Summary
In this week, you will not just learn to code; you will learn to be a **professional**. You will adopt standards that allow you to build systems that can grow, scale, and survive the test of time.
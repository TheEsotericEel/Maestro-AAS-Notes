# Lesson 05: Keeping it Clean

## 1. The Core Philosophy
Code formatting is not about aesthetics; it is about **cognitive ergonomics**. Just as a book with no paragraphs, tiny margins, and inconsistent fonts is exhausting to read, poorly formatted code exhausts the developer's brain.

> "Style is the dress of thought." — *Lord Chesterfield*

## 2. The Standard: PEP 8
In Python, we do not guess. We follow **PEP 8**, the official Style Guide for Python Code.

### Key Tenets
1.  **Indentation**: **4 Spaces**. Never tabs. A mix of tabs and spaces will crash Python 3.
2.  **Line Length**: A maximum of **79 characters**. This allows developers to have multiple files open side-by-side.
3.  **Whitespace**: Use blank lines to separate "paragraphs" of thought.

## 3. Vertical Rhythm
Code has a rhythm.
*   **Functions**: Separated by 2 blank lines.
*   **Methods (inside classes)**: Separated by 1 blank line.
*   **Logical Blocks**: Internal steps within a function are separated by 1 blank line (like paragraphs).

### Example: Finding the Rhythm
**Bad (The Wall of Text)**:
```python
def calculate_grade(score):
    if score >= 90: return 'A'
    elif score >= 80: return 'B'
    else: return 'F'
def main():
    s=int(input("Enter:"))
    g=calculate_grade(s)
    print(g)
```

**Good (The Newspaper)**:
```python
def calculate_grade(score: int) -> str:
    if score >= 90:
        return 'A'
    
    if score >= 80:
        return 'B'
        
    return 'F'


def main():
    user_score = int(input("Enter score: "))
    
    grade = calculate_grade(user_score)
    
    print(f"Final Grade: {grade}")
```

## 4. Horizontal Spacing
Whitespace *within* a line ("breathing room") drastically improves readability.

*   **Operators**: Always surround assignment (`=`) and comparison (`==`, `<`, `>`) operators with spaces.
    *   `x=y+1` (Bad)
    *   `x = y + 1` (Good)
*   **Arguments**: Space after comma.
    *   `func(a,b)` (Bad)
    *   `func(a, b)` (Good)

## 5. Automated Enforcement
Professional Engineers do not format code manually. We use **Linters** and **Formatters**.
*   **Black**: The uncompromising code formatter.
*   **Ruff / Flake8**: Enforce PEP 8 rules.

## 6. Summary
If you spend mental energy parsing the *layout* of the code, you have less energy to understand the *logic*. Keep it clean, standard, and boring.

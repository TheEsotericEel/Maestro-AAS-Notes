# Lesson 06: Making Code Instantly Readable

## 1. The Core Philosophy
> "Code should be written to minimize result-time." — *The Pragmatic Programmer*

Your goal is to minimize **Cognitive Load**: the amount of working memory required to process what the code is doing.

## 2. The Newspaper Metaphor
Good code structures itself like a newspaper article:
1.  **Headline**: The Function Name (High-level abstract).
2.  **Lead Paragraph**: The Docstring (Summary).
3.  **Details**: The Main Logic.
4.  **Footnotes**: The Helper Functions (Low-level details).

A reader should be able to scan the "Headlines" (function names) and understand the system without reading the "Body" (implementation).

## 3. Techniques for Instant Readability

### A. Explaining Variables
Avoid "Magic Numbers" and complex conditions. Extract them into variables with meaningful names.

**High Cognitive Load**:
```python
if user.age > 18 and user.country == 'US' and not user.has_debt:
    grant_loan()
```
*Issue*: The reader has to pause and calculate the logic. "Okay, over 18... US... no debt... that means...?"

**Low Cognitive Load**:
```python
is_adult = user.age > 18
is_local = user.country == 'US'
is_solvent = not user.has_debt

if is_adult and is_local and is_solvent:
    grant_loan()
```
*Benefit*: The variables explain *what* the conditions represent.

### B. The Early Return (Guard Clauses)
Deep nesting (`if` inside `if` inside `if`) pushes the reader's stack memory. Use **Guard Clauses** to handle invalid cases immediately and return/exit.

**Deep Nesting (The Arrow Code)**:
```python
def process_payment(user, amount):
    if user.is_active:
        if amount > 0:
            if user.has_funds(amount):
                user.balance -= amount
                return True
    return False
```

**Guard Clauses (Flat)**:
```python
def process_payment(user, amount):
    if not user.is_active:
        return False
        
    if amount <= 0:
        return False
        
    if not user.has_funds(amount):
        return False
        
    # The 'Happy Path' is unindented and clear
    user.balance -= amount
    return True
```

## 4. The 60-Second Scan Test
Open your file. Scroll through it for 60 seconds.
*   Do you know *where* the main logic is?
*   Do you know *what* the component does?
*   Or do you see a blur of implementation details?

## 5. Summary
Write code for the "tired" version of yourself. If it requires 100% brainpower to understand now, it will be indecipherable to you in six months.

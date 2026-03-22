# Lesson 16: Refactoring with Confidence

## 1. The Core Philosophy
> "Refactoring is changing the internal structure of software to make it easier to understand and cheaper to modify without changing its observable behavior." — *Martin Fowler*

Refactoring is not "rewriting". It is **restructuring**.

## 2. The Mechanics: The Two Hats
You can never wear both hats at once.
1.  **The Refactoring Hat**: You clean up code. You do NOT add functionality. Tests must pass at all times.
2.  **The Features Hat**: You add functionality. You do NOT clean up code. Tests can fail (temporarily).

## 3. Core Refactoring Moves

### Extract Method
The most common refactor. Take a chunk of code that "does something" and move it into a function named *after* what it does.

**Before**:
```python
def print_owing():
    print("*****************")
    print("** Customer Owes **")
    print("*****************")
    # ... calculation ...
```

**After**:
```python
def print_banner():
    print("*****************")
    print("** Customer Owes **")
    print("*****************")

def print_owing():
    print_banner()
    # ... calculation ...
```

### Rename Variable
Clarity is king. If you understand what a variable `d` does after staring at it for 5 minutes, rename it to `days_elapsed` immediately. Minimize the "WTF/minute" metric for the next reader.

## 4. The Jenga Metaphor
Refactoring is like Jenga.
1.  Identify a block (code chunk).
2.  Gently remove it (extract method).
3.  Place it on top (call the function).
4.  **Crucial Step**: Check if the tower is standing (Run Tests).

If you move 10 blocks without checking, the tower *will* fall, and you won't know which block caused it.

## 5. Summary
Refactoring is payment on technical debt. If you don't pay it, the interest (complexity) will eventually bankrupt the project.

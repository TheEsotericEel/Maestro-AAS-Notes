# Lesson 10: Designing Functions that Can Be Reused Anywhere

## 1. The Core Philosophy
A function should be a "Black Box" or a "Lego Brick". It shouldn't care *where* it is being used. It should just accept inputs and return outputs.

## 2. Pure Functions
In Computer Science, a **Pure Function** has two properties:
1.  Its return value is the same for the same arguments (Deterministic).
2.  It has no side effects (doesn't print, doesn't read global variables, doesn't mutate external state).

**Goal**: Maximize the number of pure functions in your codebase.

## 3. The "Environment Agnostic" Rule
Your function should not know it is running in a Console App.
*   **Violation**: A function that calls `input()` or `print()`. It is now married to the Console. It cannot be used in a Web App or a GUI.
*   **Correction**: Pass data in as arguments. Return data as values.

### The Refactor

**Environment Coupled (Bad)**:
```python
# This function is useless for a Web API
def calculate_tax():
    price = float(input("Enter price: ")) # Coupled to Console Input
    print(price * 1.05)                   # Coupled to Console Output
```

**Environment Agnostic (Professional)**:
```python
# This function can be used ANYWHERE (Web, Game, Mobile, CLI)
def calculate_tax(price: float) -> float:
    return price * 1.05
```

## 4. Separation of Concerns (I/O vs Logic)
Separate your code into three distinct layers:
1.  **Input Layer**: Talks to User (Inputs).
2.  **Logic Layer**: Does the Math (Pure Functions).
3.  **Output Layer**: Talks to User (Prints/Displays).

### The Architecture
```python
# --- Logic Layer (The Brains) ---
def add(a, b): return a + b

# --- Interface Layer (The Mouth) ---
def main():
    # 1. Input
    x = int(input("N1: "))
    y = int(input("N2: "))
    
    # 2. Logic (Delegated to Pure Function)
    result = add(x, y)
    
    # 3. Output
    print(f"Result: {result}")
```

## 5. Dependency Injection (Simplified)
Don't use Global Variables. They are "hidden inputs".
*   **Bad**: Function uses `TAX_RATE` (global). If you want to calculate tax for a different country, you have to change the global variable.
*   **Good**: Function takes `tax_rate` as an argument. You can simply pass a different rate.

## 6. Summary
Ask yourself: "Could I copy-paste this function into a totally different project and have it work immediately?"
*   If **Yes**: You are an Engineer.
*   If **No**: You are a Scripter. Refactor.

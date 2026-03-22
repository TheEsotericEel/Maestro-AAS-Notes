# Lesson 07: Turning Long Scripts into Sharp Functions

## 1. The Core Philosophy
> "The first rule of functions is that they should be small. The second rule of functions is that they should be smaller than that." — *Robert C. Martin*

In PY101, you wrote **Scripts**: top-to-bottom lists of instructions.
In CS101, we write **Modular Software**: discrete, reusable components that interact.

## 2. The Single Responsibility Principle (SRP)
Every function should do **one thing**, do it well, and do it only.

### Diagnosis: The "And" Test
Describe your function. If the word "and" appears, it is doing too much.
*   "This function calculates the tax **and** prints the receipt." -> **Split it.**
*   "This function validates the input **and** saves to the database." -> **Split it.**

## 3. The Anatomy of a Function
Focus on **High Cohesion** and **Low Coupling**.
*   **Cohesion**: Every line in the function relates to a single purpose.
*   **Coupling**: The function relies on as few external things (globals) as possible.

## 4. Refactoring Strategy: Input-Process-Output
Most scripts follow a pattern: Get Data -> Process Data -> Display Data. Split these into three layers.

### The Monolith (Bad)
```python
# A single script doing everything
import math

r = float(input("Radius: "))  # Input
if r < 0:
    print("Error")
else:
    area = math.pi * (r ** 2) # Process
    print(f"Area: {area}")    # Output
```

### The Modular Approach (Good)
```python
import math

def get_valid_radius():
    """Handles Input (I/O)."""
    radius = float(input("Radius: "))
    if radius < 0:
        raise ValueError("Radius cannot be negative.")
    return radius

def calculate_circle_area(radius):
    """Handles Processing (Pure Logic)."""
    return math.pi * (radius ** 2)

def display_result(area):
    """Handles Output (I/O)."""
    print(f"Area: {area:.2f}")

# The Coordinator (Main)
def main():
    try:
        r = get_valid_radius()
        a = calculate_circle_area(r)
        display_result(a)
    except ValueError as e:
        print(f"Error: {e}")
```

## 5. Why Decomposition Matters
1.  **Testability**: You can test `calculate_circle_area(10)` without user input.
2.  **Reusability**: You can use `calculate_circle_area` in a web app, a game, or a report without changing a line.
3.  **Debuggability**: If the calculation is wrong, you know exactly where to look.

## 6. Summary
Stop writing scripts. Start building machines. Each function is a gear. It should spin perfectly on its own.

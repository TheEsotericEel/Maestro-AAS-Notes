# Assembling Functions into Pipelines

## 1. Concept: Composition and Orchestration
> **Definition**: The architectural pattern of connecting independent, pure functions into a sequence where the output of one becomes the input of the next.

This separation creates a clear distinction between the **Workers** (Functions that do the job) and the **Manager** (Function that tells them what to do).

## 2. The "Why": The Single Responsibility Principle
Why separate orchestration from logic?
1.  **Reusability**: `clean_data()` can be used anywhere if it doesn't also try to `save_to_db()`.
2.  **Testability**: You can test the workers individually without running the whole pipeline.
3.  **Clarity**: The `main()` function reads like a table of contents for the program.

## 3. The "How": The Main Function
The `main()` function should contain almost **no logic**. It should only contain **control flow**.

### The Orchestration Pattern
```python
def main():
    # 1. Acquire Resources (Input)
    data = fetch_input()

    # 2. Pipeline Execution (Process)
    processed = step_one(data)
    final_result = step_two(processed)

    # 3. Release Results (Output)
    display(final_result)
```

## 4. Examples: The Data Pipeline

### Bad: The God Function (Coupled)
```python
def do_everything():
    # Getting input
    data = input("Enter data: ")
    # Logic mixed with I/O
    if len(data) > 5:
        print("Too long")
    else:
        # Saving mixed with logic
        db.save(data)
```
*Critique*: You cannot test the length check without running the input/db code.

### Good: The Pipeline (Decoupled)
```python
def get_input_data():
    return input("Enter data: ")

def validate_length(d):
    return len(d) <= 5

def save_to_db(d):
    db.save(d)

def main():
    data = get_input_data()
    if validate_length(data):
        save_to_db(data)
    else:
        print("Too long")
```
*Critique*: `validate_length` is now a pure function. It is easy to test `validate_length("abc")` -> `True`.

## 5. Truth: Functions Should Be Shy
Functions should be introvert.
*   They should not look at global variables (The world outside).
*   They should not talk to functions they weren't introduced to.
*   They should only know about their arguments and their return values.

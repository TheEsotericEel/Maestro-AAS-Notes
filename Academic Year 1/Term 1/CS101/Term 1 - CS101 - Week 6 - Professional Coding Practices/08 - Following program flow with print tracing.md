# Lesson 08: Following Program Flow with Print Tracing

## 1. The Core Philosophy
Code execution is invisible. To fix a bug, you must make the invisible visible.
While professional environments use dedicated **Logging Frameworks** or **Debuggers**, the humble `print` statement remains the fastest tool for immediate feedback.

> "The most effective debugging tool is still careful thought, coupled with judiciously placed print statements." — *Brian Kernighan*

## 2. Observability Strategy
Don't just print "here". Print **State** and **Flow**.

### Types of Traces
1.  **Flow Trace**: "Did the program enter this `if` block?"
2.  **State Trace**: "What is the value of `user_id` at this exact microsecond?"

### The Tagging Standard
Always prefix debug prints with a tag (e.g., `[DEBUG]` or `[TRACE]`) so they are easy to spot and remove later.

```python
# Bad
print("here")
print(x)

# Good
print(f"[DEBUG] Validating User. Status: {user.status}")
print(f"[TRACE] Entering payment calculation loop.")
```

## 3. The "Heisenbug" and `repr()`
Sometimes what you *see* is not what you *have*.
*   The string `"5"` looks like the number `5` in standard output.
*   The string `" "` (space) looks like `""` (empty) if not careful.

**Solution**: Use `repr()` (Representation) to see the raw data.

```python
value = "5 "  # Note the trailing space

print(f"Value is: {value}")         # Output: Value is: 5 
# Reader thinks: "It's 5. Why is the math failing?"

print(f"Value is: {repr(value)}")   # Output: Value is: '5 '
# Reader realizes: "Aha! It's a string with a space!"
```

## 4. The Binary Search Method
If your script crashes "somewhere" in 100 lines of code, don't read line by line. Use Computer Science.
1.  Place a print statement at line 50.
2.  Run code.
    *   **Prints?** The crash is in lines 51-100.
    *   **Doesn't Print?** The crash is in lines 1-49.
3.  Repeat until the bug is trapped.

## 5. Summary
Debugging is not guessing. It is the scientific method applied to code. Form a hypothesis ("I think it enters the `if` block"), conduct an experiment (add a print), and observe the results.

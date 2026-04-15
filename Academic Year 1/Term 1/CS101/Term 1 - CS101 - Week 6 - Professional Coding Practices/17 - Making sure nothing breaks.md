# Lesson 17: Making Sure Nothing Breaks (Regression)

## 1. The Core Philosophy
A **Regression** is when you fix a bug and accidentally break something that was working. It is the most embarrassing mistake in Software Engineering.
**Automated Tests** are the only defense against regression.

## 2. The Safety Net
Imagine walking a tightrope (coding).
*   **Without Tests**: One slip, and you fall to your death.
*   **With Tests**: You have a net. You slip, the net catches you (Test Fails), and you climb back up.

## 3. The Green-Red-Green Cycle (TDD)
This is the rhythm of professional development.
1.  **Red**: Write a test that fails (because the feature isn't built yet).
2.  **Green**: Write just enough code to make the test pass.
3.  **Refactor**: Clean up the code. (The test ensures you didn't break it).

## 4. Practical Implementation: The Test Suite
A "Suite" is a collection of tests that verify the system.

```python
# The Code
def add(a, b):
    return a + b

# The Suite (Regression Net)
def test_suite():
    tests = [
        (1, 1, 2),       # Standard
        (100, 100, 200), # Large
        (-5, 5, 0),      # Negative
        (0, 0, 0)        # Zero
    ]
    
    for a, b, expected in tests:
        result = add(a, b)
        assert result == expected, f"Failed: {a}+{b} should be {expected}"
    
    print("All tests passed.")

# Run it every time you change the code!
if __name__ == "__main__":
    test_suite()
```

## 5. Summary
Tests allow you to move fast. Without tests, you walk slowly because you are afraid of breaking things. With tests, you can sprint, because the net will catch you.

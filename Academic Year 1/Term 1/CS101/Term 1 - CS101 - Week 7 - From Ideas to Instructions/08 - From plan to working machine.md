# Translation: From Pseudocode to Python

## 1. The Translator's Mindset

### What is it?
Once you have valid Pseudocode, the "Thinking" phase is over. The "Translation" phase begins. This is a mechanical process of mapping logic Concept A to Syntax B.

### Why does it matter?
Trying to design the logic *while* worrying about syntax leads to cognitive overload. By separating them, you can focus purely on the grammar of the language.

### The Dictionary of Translation
| Pseudocode Concept | Python Syntax |
| :--- | :--- |
| **Store** / **Set** | `variable = value` |
| **Display** / **Show** | `print()` |
| **Ask** / **Input** | `input()` |
| **Repeat 10 times** | `for i in range(10):` |
| **Repeat While** | `while condition:` |
| **Check If** | `if condition:` |
| **Otherwise** | `else:` |

---

## 2. The Incremental Build Strategy

**Gall's Law:** "A complex system that works is invariably found to have evolved from a simple system that worked."

Do not write 100 lines of code and then hit "Run."
1.  **Skeleton**: Write the main control flow (loops/ifs) with `pass` or print statements. -> **Run it.**
2.  **Muscle**: Implement the variables and data structures. -> **Run it.**
3.  **Skin**: Add the detailed logic and formatting. -> **Run it.**

---

## 3. Practical Examples

### Example 1: The Loop Implementation

**Pseudocode Plan**
```text
1. Set total to 0
2. For numbers 1 to 5:
    2.1 Add number to total
3. Print total
```

**Step 1: The Skeleton (Verification of Flow)**
```python
total = 0
for i in range(1, 6):
    print(f"Looping... {i}") # Debug print
print("Done")
```
*Run this. Does it loop 5 times? Yes. Proceed.*

**Step 2: The Logic (Implementation)**
```python
total = 0
for i in range(1, 6):
    total = total + i
print(total)
```
*Run this. Is the answer 15? Yes. Done.*

### Example 2: The Conditional

**Pseudocode Plan**
```text
IF Age < 18:
    Print "Minor"
ELSE:
    Print "Adult"
```

**Python Translation**
```python
age = int(input("Enter age: ")) # Recall: Input returns string, must cast to int.

if age < 18:
    print("Minor")
else:
    print("Adult")
```

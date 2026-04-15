# Manual Trace Execution

## 1. The Human CPU

### What is it?
Manual Tracing (or "Dry Running") is the act of simulating a computer's execution stack in your mind or on paper. You become the CPU. You execute one line at a time, update variables, and check conditions.

### Why does it matter?
Computers are fast but opaque. You cannot "see" the logic happening inside the silicon. Tracing makes the invisible visible. It is the primary tool for finding infinite loops and logic drift.

---

## 2. The Mechanics of State Tracking

You must track the **State** of the application. State is simply the current value of all variables at a specific moment in time.

**The Grid System**
Create a grid. Every column is a variable. Every row is a step.

**Code:**
```python
1. x = 1
2. y = 4
3. while x < y:
4.     x = x * 2
5.     y = y + 1
```

**Trace:**
| Step | Line | `x` (Memory) | `y` (Memory) | Check `x < y` |
| :--- | :--- | :--- | :--- | :--- |
| 1 | 1 | **1** | - | - |
| 2 | 2 | 1 | **4** | - |
| 3 | 3 | 1 | 4 | **True** (1 < 4) |
| 4 | 4 | **2** | 4 | - |
| 5 | 5 | 2 | **5** | - |
| 6 | 3 | 2 | 5 | **True** (2 < 5) |
| 7 | 4 | **4** | 5 | - |
| 8 | 5 | 4 | **6** | - |
| 9 | 3 | 4 | 6 | **True** (4 < 6) |
| 10 | 4 | **8** | 6 | - |
| 11 | 5 | 8 | **7** | - |
| 12 | 3 | 8 | 7 | **False** (8 !< 7) -> EXIT |

*Result*: The loop runs 3 times. Final values: x=8, y=7.

---

## 3. Detecting Common Errors

### The Infinite Loop
If your table layout shows `x` staying constant while `y` grows, or the condition never flips to False, you have mathematically proven an infinite loop.

### The Off-By-One
If you intended to loop 5 times, but your table shows the loop condition becoming False after step 4, you have an Off-By-One error.

---

## 4. The Rubber Duck Method

If a table is too complex, speak it out loud.
1.  Grab a Rubber Duck (or inanimate object).
2.  Explain line 1.
3.  Explain line 2.
4.  Explain line 3.
5.  *“...and then I check if x is greater than zero... oh wait, x is -1 here. That’s why it crashed.”*

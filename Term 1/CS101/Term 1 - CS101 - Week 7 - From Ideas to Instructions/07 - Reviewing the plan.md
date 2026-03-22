# Algorithmic Verification and Dry Running

## 1. The Art of Self-Correction

### What is it?
Verification is the process of proving your code works *before* you run it. The primary method for this is **Desk Checking** (or "Dry Running")—manually stepping through the logic with a pencil and paper.

### Why does it matter?
Running code to see if it works is "Brute Force" debugging. It is slow and reactive. Desk Checking is proactive. It builds a mental model of the computer's state at every step.

---

## 2. The Trace Table

A Trace Table tracks the value of every variable at every line of execution.

**Code:**
```python
1. x = 5
2. y = 10
3. while x < y:
4.     x = x + 2
5.     y = y + 1
```

**Trace Table:**
| Line | x | y | Condition (x < y) |
| :--- | :--- | :--- | :--- |
| 1 | 5 | - | - |
| 2 | 5 | 10 | - |
| 3 | 5 | 10 | True (5 < 10) |
| 4 | 7 | 10 | - |
| 5 | 7 | 11 | - |
| 3 | 7 | 11 | True (7 < 11) |
| 4 | 9 | 11 | - |
| 5 | 9 | 12 | - |
| 3 | 9 | 12 | True (9 < 12) |
| 4 | 11 | 12 | - |
| 5 | 11 | 13 | - |
| 3 | 11 | 13 | True (Wait.. infinite loop?) |

*Analysis*: By tracing, we realize that both X and Y increase. X increases by 2, Y by 1. X will eventually catch y? 
Let's check math: 
Diff is 5. 
Loop 1: Diff is 4 (7 vs 11). 
Loop 2: Diff is 3 (9 vs 12).
Loop 3: Diff is 2 (11 vs 13).
It will terminate. But without the trace, we might guess.

---

## 3. The MECE Principle

**Mutually Exclusive, Collectively Exhaustive.**

When verifying conditionals (`if/elif/else`), ask:
1.  **Mutually Exclusive**: Can an input trigger *two* branches? (It shouldn't).
    *   *Bad*: `if x > 5` and `if x > 10`. (12 triggers both).
2.  **Collectively Exhaustive**: Does an input trigger *zero* branches? (It shouldn't).
    *   *Bad*: `if x < 0` and `if x > 0`. (0 triggers nothing).

---

## 4. The Critic's Checklist

Before you write code, audit your pseudocode:
1.  **The Init Check**: Are all variables given a value before they are used?
2.  **The Loop Termination Check**: Does the loop condition eventually become False?
3.  **The Gaps Check**: What happens if the list uses 0-indexing vs 1-indexing?
4.  **The Type Check**: Are you trying to add a String to an Integer?

> "Be the harshest critic of your own plans. It hurts less than a compiler error."

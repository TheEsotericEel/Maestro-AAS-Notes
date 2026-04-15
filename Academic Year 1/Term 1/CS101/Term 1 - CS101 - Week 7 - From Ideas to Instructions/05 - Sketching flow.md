# Visualizing Control Flow

> "A flow chart is a graphical representation of an algorithm."

## 1. The Power of Visualization

### What is it?
Visualizing flow is the practice of drawing the execution path of a program before writing it. This often takes the form of a **Flowchart** or a **Decision Tree**.

### Why does it matter?
Text is linear; Logic is branching. It is difficult to see dead ends or infinite loops in text. In a diagram, a line that goes nowhere is immediately obvious.

### Standard Symbols
| Shape | Meaning | Example |
| :--- | :--- | :--- |
| **Oval** | Start / End | `START`, `EXIT` |
| **Rectangle** | Process / Action | `x = x + 1`, `Calculate Total` |
| **Diamond** | Decision (Branch) | `Is x > 10?` (Yes/No lines) |
| **Parallelogram** | Input / Output | `Print x`, `Read File` |

---

## 2. The Law of Conservation of Data

**"Every input must have a destination."**

When you draw a Diamond (Decision), you usually create two paths (Yes/No). You must trace **both** paths to their conclusion.
*   **The Happy Path**: usage is correct (User enters "10").
*   **The Edge Path**: usage is incorrect (User enters "-5").

If your diagram has a path that just stops without joining an End state or looping back? That is a bug.

---

## 3. Practical Examples

### Example 1: The Login Flow
**Task**: Validate user credentials.

**Logic Trace**:
1.  **Start**
2.  **Input**: Get Username/Password.
3.  **Decision**: Is Username empty?
    *   **Yes**: Print "Error" -> **End**.
    *   **No**: Continue.
4.  **Decision**: Check DB. match?
    *   **No**: Print "Invalid" -> **End**.
    *   **Yes**: Log user in -> **End**.

### Example 2: The "Marble Run" (Range Checking)
Imagine dropping a marble (a number) into your logic.

**Visualizing Gaps**:
```text
      [ Input: Score ]
            |
      < Is x < 50? >
     /              \
  (Yes)            (No)
    |                |
 [Fail]       < Is x > 60? >  <-- GAP! What about 50-60?
             /              \
          (Yes)            (No)
            |                |
         [Pass]           [ ??? ]
```
In this visualization, if you drop the number `55`, it falls through the "No" branch of the first diamond, and the "No" branch of the second diamond (assuming the second check was intended to be `> 50`). If there is no logic there, the program fails.

## 4. Execution Strategy

1.  **Drafting**: Use a whiteboard or paper. Do not use software logic tools yet (they slow you down).
2.  **Tracing**: Run your "finger" along the lines.
3.  **Refining**: Once the logic holds water, translate it to Pseudocode.

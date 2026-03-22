# Lesson 06: Modeling Real-World Calculations

## 🎯 End Goal
To translate complexity into clarity. You will learn to take a messy, real-world narrative and reconstruct it as a clean, logical, and executable Python program.

## 🧠 Core Concepts

### 1. Abstraction (The Model)
The map is not the territory. A computer program is not the real world; it is a **model** of the real world.
*   **Real World**: "I went to the store, bought 3 apples for $0.50 each, and paid with a $5 bill."
*   **Model**: variables (`cost`, `qty`, `payment`) and algorithms (`change = payment - (cost * qty)`).

### 2. Magic Numbers (The Enemy)
A "Magic Number" is a direct numeric value used in code without context.
*   **Bad**: `total = x * 1.08` (What is 1.08?)
*   **Good**: `TAX_RATE = 1.08`; `total = x * TAX_RATE` (Ah, it's the tax rate.)

> [!IMPORTANT]
> **Use Constants**: If a number represents a fixed universal truth (like Pi or Tax Rate), give it a name in `ALL_CAPS`.

### 3. Stepwise Refinement
Do not try to solve the whole problem in one line. Break it down.
*   **Input**: Get the raw data.
*   **Process**: Calculate intermediate values.
*   **Output**: Display the final result.

## 📝 The Transformation Process

### Scenario: The Pizza Party
*Problem*: You are ordering pizzas for a party. Each pizza has 8 slices. There are 4 guests. Each guest wants 3 slices. How many pizzas do you need?

#### Step 1: The "Napkin Math" (Bad Code)
```python
print((4 * 3) / 8)
# Output: 1.5
```
*Critique*: This works, but it explains nothing. If we look at this code tomorrow, we won't know what `4`, `3`, or `8` represent.

#### Step 2: The Structured Model (Good Code)
```python
# 1. Define Constants
SLICES_PER_PIZZA = 8

# 2. Define Variables (Inputs)
guests = 4
slices_per_guest = 3

# 3. Process (The Logic)
total_slices_needed = guests * slices_per_guest
pizzas_needed = total_slices_needed / SLICES_PER_PIZZA

# 4. Output
print(pizzas_needed)
```
*Critique*: This is self-documenting. We can read the logic like English.

## ⚡ Associations
*   **Noun** -> **Variable** (`guests`)
*   **Verb** -> **Operator** (`*`, `/`)
*   **Fixed Value** -> **Constant** (`SLICES_PER_PIZZA`)

## ⚠️ Traps and Pitfalls

| Mistake | Code | Why it fails |
| :--- | :--- | :--- |
| **Ambiguous Units** | `duration = 5` | Is that 5 seconds? Minutes? Hours? <br> *Fix*: `duration_minutes = 5`. |
| **Hardcoding** | `print(19.99 * 1.08)` | You can't change the price or tax rate without rewriting the code. |
| **One-Liners** | `print((x+y)*z/a)` | You saved 3 lines of code but lost 10 minutes of reading time. **Optimize for reading, not writing.** |

## 🔍 Professional Standard: Self-Documenting Code
The goal of modeling is not just to get the right answer. It is to write code that explains the *process* of getting the answer to another human being.

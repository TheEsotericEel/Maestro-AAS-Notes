# Writing a Structured Problem Statement

## 1. Concept: Design by Contract
> **Definition**: A Problem Statement is a formal specification that defines the **Contract** between the caller (User/Client) and the callee (Function/Program). It rigorously defines the Inputs (Pre-conditions), Outputs (Post-conditions), and Success Criteria (Invariants).

This concept maps directly to **Bertrand Meyer's** principle of **Design by Contract (DbC)**, which treats software component interactions as legal contracts.

## 2. The "Why": The Black Box Principle
Why do we define contracts before writing code?
1.  **Implementation Agnosticism**: We define *what* the box does, not *how*. This prevents "implementation bias" (thinking about loops before understanding the data).
2.  **Testability**: A clear contract writes its own tests. If you know "Input A yields Output B," you have a test case.
3.  **robustness**: By defining valid inputs (pre-conditions), we protect our logic from undefined states.

## 3. The "How": The I-O-S Framework
To structure a problem statement, we define three components:

### 1. Inputs (The Domain)
What are the raw materials? Be specific about types and constraints.
*   *Vague*: "A number."
*   *Specific*: "A positive integer between 1 and 100."

### 2. Outputs (The Range)
What is the product?
*   *Vague*: "The answer."
*   *Specific*: "A floating-point number rounded to 2 decimal places representing USD."

### 3. Success Criteria (The Acceptance Test)
How do we mathematically prove it works? Define specific input-output pairs.

## 4. Examples: Structuring the Contract

### Example 1: The Palindrome Checker
**Problem**: We need to verify if a word is a palindrome.

| Component | Specification |
| :--- | :--- |
| **Purpose** | Determine if a given text string reads identical forwards and backwards, ignoring casing. |
| **Input** | A string `s`. May contain alphanumeric characters. |
| **Output** | A `Boolean`. `True` if palindrome, `False` otherwise. |
| **Edge Cases** | Empty string -> `True` (Trivial identity). Single char -> `True`. |

**Success Criteria**:
*   `"Racecar"` -> `True` (Case insensitive)
*   `"hello"` -> `False`
*   `"12321"` -> `True`

### Example 2: The Tip Calculator
**Problem**: Calculate the tip for a bill.

| Component | Specification |
| :--- | :--- |
| **Purpose** | Calculate the monetary value of a tip based on bill total and service quality. |
| **Input** | `Bill Amount` (Float > 0), `Quality` (Enum: Poor, Good, Great). |
| **Output** | `Tip Amount` (Float, rounded to 2 decimals). |

**Success Criteria**:
*   `100.00`, `Good` (20%) -> `20.00`
*   `50.00`, `Poor` (10%) -> `5.00`

## 5. Critical Distinction: Constraint vs. Logic
A common error is mixing *constraints* with *logic*.

*   **Constraint (Input Definition)**: "The input list must not be empty." (This is part of the contract/problem statement).
*   **Logic (Implementation)**: "If list is empty, raise error." (This is code).

Keep the problem statement focused on **what is allowed**, not **how it is enforced**.

## 6. Truth: "A Problem Well-Stated is Half-Solved"
Charles Kettering, former head of research at GM, famously said:
> "A problem well-stated is a problem half-solved."

If you cannot write the I-O-S contract, you do not understand the problem. Do not open your IDE until this contract is written.

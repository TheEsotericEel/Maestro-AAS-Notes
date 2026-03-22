# Breaking Down into Subproblems

## 1. Concept: Decomposition (Divide and Conquer)
> **Definition**: The process of breaking a complex system into smaller, more manageable, and independent subsystems that can be designed, implemented, and executed separately.

This is the single most important skill in Computer Science. As **René Descartes** outlined in *Discourse on the Method* (1637): "Divide each difficulty into as many parts as is feasible and necessary to resolve it."

## 2. The "Why": Complexity Management
Why do we decompose?
1.  **Cognitive Load**: The human brain can only hold ~7 chunks of information at once (Miller's Law). A "Monolith" problem exceeds this. Subproblems fit.
2.  **Isolation**: Bugs in Subproblem A are easier to fix if they aren't tangled with Subproblem B.
3.  **Parallelism**: You can't hire 5 people to write one function. You *can* hire 5 people to write 5 sub-modules.

## 3. The "How": The Granularity Rule
How small should a subproblem be?
*   **Too Big**: "Build the User System." (Contains database, validation, UI, auth).
*   **Too Small**: "Define the variable X." (This is a line of code, not a problem).
*   **Just Right**: "Validate the User's Password." (Atomic, testable, complete).

### Strategy: Recursive Decomposition
1.  Take the Big Problem.
2.  Split it into 3-5 Major Components.
3.  Take Component 1. Split it into 3-5 Sub-Components.
4.  Repeat until every leaf node is "Solvable in one Function."

## 4. Examples: Decomposing a System

### The E-Commerce Checkout
**Level 0: The Problem**
> "Process a User's Order."

**Level 1: Verification**
1.  Validate User Account. (Active? Not banned?)
2.  Validate Cart Inventory. (Items in stock?)
3.  Verify Payment Method. (Funds available?)

**Level 2: Execution**
4.  Lock Inventory. (Prevent others from buying).
5.  Charge Card. (Interact with Stripe/PayPal).
6.  Create Order Record. (Database write).
7.  Send Confirmation Email. (SMTP Service).

**Level 3: Cleanup**
8.  Empty Cart.
9.  Log Transaction.

### The "Atomic" Function Test
Can you write a docstring for the subproblem that describes ONE responsibility?
*   `def process_order()`: Too broad. Responsibilities: Validate, Charge, Save, Email.
*   `def send_email()`: Atomic. Responsibility: Email.

## 5. Critical Rule: Independent Slices
Subproblems should be as independent as possible (High Cohesion, Low Coupling).
*   **Bad**: The "Email" function also calculates the tax.
*   **Good**: The "Tax" function returns a float. The "Email" function takes a float as input.

## 6. Truth: The Elephant
> "How do you eat an elephant?"
> "One bite at a time."

Attempting to swallow the elephant whole (coding without decomposition) leads to choking (project failure).

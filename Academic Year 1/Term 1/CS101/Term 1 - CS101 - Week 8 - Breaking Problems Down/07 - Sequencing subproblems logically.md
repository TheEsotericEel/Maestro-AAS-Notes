# Sequencing Subproblems Logically

## 1. Concept: Dependency Resolution
> **Definition**: The process of ordering tasks such that no task is attempted before its prerequisites are met. This creates a Directed Acyclic Graph (DAG) of execution.

This is logic, not preference. If Task B requires data produced by Task A, Task A **must** happen first. This is a **Hard Dependency**.

## 2. The "Why": Data Availability
Programs crash when they try to access data that doesn't exist yet (UnboundLocalError, NullReferenceException). logical sequencing guarantees data availability.

It also reveals:
1.  **Blockers**: Steps that halt the entire pipeline.
2.  **Parallelism**: Steps that share no dependencies and can be run simultaneously (Async).

## 3. The "How": Needs vs. Produces
For every subproblem scratchpad:
1.  **Needs**: What inputs does this function *require* to run?
2.  **Produces**: What outputs does this function *create*?

**Rule**: You cannot place a card on the timeline until all of its "Needs" have been "Produced" by previous cards.

## 4. Examples: Topological Sorting

### The Retail Transaction
**Tasks**:
A. Send Receipt Email
B. Calculate Tax
C. Charge Credit Card
D. Get Cart Total

**Dependency Analysis**:
*   A (Email) Needs: `Transaction ID` (from C).
*   B (Tax) Needs: `Cart Total` (from D).
*   C (Charge) Needs: `Final Total` (Cart + Tax).
*   D (Get Total) Needs: `Cart Data`.

**Resolution (The Sequence)**:
1.  **D (Get Total)**: Produces `Cart Total`.
2.  **B (Calculate Tax)**: Uses `Cart Total` -> Produces `Tax Amount`.
    *   *Intermediate Step*: `Final Total = Cart Total + Tax Amount`.
3.  **C (Charge Card)**: Uses `Final Total` -> Produces `Transaction ID`.
4.  **A (Send Email)**: Uses `Transaction ID` -> Produces `Sent Status`.

### Visualization: The Waterfall
```text
[Get Total] --> [Calc Tax] --> [Charge Card] --> [Email]
```

### Parallel Opportunities
**Scenario**: We need to load user profile AND load latest news feed.
*   Task A: Load Profile (Needs: UserID).
*   Task B: Load News (Needs: Region).
*   **Analysis**: A does not need B. B does not need A.
*   **Sequence**: Run A and B in parallel (Wait for both). -> **Task C**: Render Page.

## 5. Common Patterns
*   **Pipeline**: A -> B -> C (Strict sequence).
*   **Fan-Out**: A triggers B, C, and D (Parallel).
*   **Fan-In**: B, C, and D finish -> E aggregates results.

## 6. Truth: The Cake Fallacy
You cannot frost the cake before you bake it.
You cannot bake it before you mix it.
You cannot mix it before you buy ingredients.
Any attempt to violate this order results in a mess, not a cake.

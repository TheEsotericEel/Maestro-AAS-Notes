# Prioritizing Tasks

## 1. Concept: Technical Triage
> **Definition**: The systematic process of ranking tasks based on quantitative metrics (Value, Cost, Risk) rather than subjective feelings.

In medical terms, **Triage** determines who gets the doctor first: the heart attack (High Priority) or the sprained ankle (Low Priority). In engineering, it determines what gets built: the crash fix or the logo redesign.

## 2. The "Why": Opportunity Cost
Every hour you spend on Task A is an hour you *cannot* spend on Task B. This is **Opportunity Cost**.
*   If Task A saves \$10 and Task B saves \$10,000, choosing Task A costs you \$9,990.
*   Without prioritization, engineers naturally gravitate towards "Fun" or "Easy" tasks, ignoring "Valuable" or "Hard" ones.

## 3. The "How": Prioritization Frameworks

### The RICE Score (Intercom)
Calculate a score for every task:
$$Score = \frac{Reach \times Impact \times Confidence}{Effort}$$
*   **Reach**: How many users will this affect?
*   **Impact**: How much value per user?
*   **Confidence**: How sure are we? (metrics vs guesses).
*   **Effort**: How many weeks/months?

### The Eisenhower Matrix (Urgency vs Importance)
| | Urgent | Not Urgent |
| :--- | :--- | :--- |
| **Important** | **Do Now** (Critical Bugs, Server Down) | **Schedule** (Architecture, refactoring) |
| **Not Important** | **Delegate** (Meetings, Emails) | **Delete** (Bike-shedding, trivial tweaks) |

## 4. Examples: Ranking the Backlog

**The Backlog**:
1.  **Task A**: Fix a crash affects 10% of users. (High Impact, Low Effort).
2.  **Task B**: Redesign the "About Us" page. (Low Impact, Medium Effort).
3.  **Task C**: Refactor the entire database. (Invisible Impact, Huge Effort).

**The Ranking**:
1.  **Priority 1 (Task A)**: "The Quick Win". High ROI. Do immediately.
2.  **Priority 2 (Task B)**: "The Filler". Do when blocked on A.
3.  **Priority 3 (Task C)**: "The Money Pit". Be very careful. Only do if strictly necessary for scale.

## 5. Critical Rule: Blockers First
If Task A requires Task B to be finished, Task B is a **Blocker**.
*   Blockers inherently inherit the priority of what they block.
*   If the "Crash Fix" (Priority 1) is blocked by "Server Access" (Priority 10), "Server Access" becomes Priority 1.

## 6. Truth: If Everything is Important...
> "If everything is high priority, nothing is high priority."

A list where every item is labeled "Critical" is merely a list of things you haven't organized yet.

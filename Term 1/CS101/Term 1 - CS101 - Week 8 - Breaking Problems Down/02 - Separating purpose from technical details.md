# Separating Purpose from Technical Details

## 1. Concept: Separation of Concerns (Requirements Level)
> **Definition**: The strict conceptual separation between **Business Logic** (the "What" and "Why") and **Implementation Detail** (the "How"). This is the foundational principle of Abstraction.

In software engineering, mixing these two layers leads to **Coupled Code**, where changing a business rule breaks the technical implementation, or changing a library requires rewriting business logic.

## 2. The "Why": Decoupling and Flexibility
Why do we rigorously separate purpose from mechanics?
1.  **Longevity**: Business rules (e.g., "Users must have a valid email") change slowly. Technology (e.g., "Store in a SQL database") changes quickly. Coupling them ties your business logic to obsolete tech.
2.  **Communication**: Stakeholders speak "Purpose" (Revenue, Users). Engineers speak "Tech" (SQL, JSON). You must be the translator.
3.  **Testability**: You can test the purpose ("Did the user get rejected?") without needing the real tech (mocking the database).

## 3. The "Who": David Parnas
**David Parnas** introduced the concept of **Information Hiding** in 1972. He argued that modules should hide their design decisions (technical details) from others, exposing only their purpose (interface).

## 4. The "How": The Leak Detector Test
To verify separation, scan your requirements or documentation for "Leaky Abstractions".

### The Forbidden Lexicon
If your **Purpose** statement contains any of these words, it is wrong:
*   `Loop`, `Array`, `Dictionary`, `String`, `Int`
*   `Database`, `SQL`, `API`, `Endpoint`, `JSON`, `XML`
*   `Click`, `Hover`, `Screen`, `Pixel`

These belong strictly in the **Technical** specification.

## 5. Examples: Purpose vs. Technical

### Case Study 1: Data Persistence
| Layer | Description |
| :--- | :--- |
| **Purpose (The What)** | "Persist the user's shopping cart so they can resume shopping later." |
| **Technical (The How)** | "Serialize the `Cart` object to JSON and write to `localStorage` with a 24h TTL." |
| **Why it Matters** | If we switch from `localStorage` to a Redis backend, the **Purpose** remains exactly the same. Only the **Technical** detail changes. |

### Case Study 2: User Validation
| Layer | Description |
| :--- | :--- |
| **Purpose (The What)** | "Ensure the user is old enough to purchase restricted items." |
| **Technical (The How)** | "Check if `user.age >= 18` using an integer comparison." |
| **Why it Matters** | "Restricted items" might change definition (e.g., alcohol vs. video games), but the technical check is just math. Separating them allows us to change the policy easily. |

### Case Study 3: Code Comments
**❌ Bad Comment (Redundant)**
```python
# Increment i by 1
i = i + 1
```
*Critique*: Tells me *what* the code does (which I can see), not *why*.

**✅ Good Comment (Purposeful)**
```python
# Move to the next student in the grading queue
i = i + 1
```
*Critique*: Explains the domain intent.

## 6. The "So What?" Recursive Test
Use this technique to distill purpose:
1.  **State the Action**: "I'm using a regex."
2.  **Ask 'So What?'**: "So I can match the email pattern."
3.  **Ask 'So What?'**: "So we ensure the user provides a reachable contact method."
    *   **Result**: "Ensure user provides a reachable contact method" is the **Purpose**. "Use a regex" is the **Technical Detail**.

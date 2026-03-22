# Writing a Clear Feature Brief

## 1. Concept: The Feature Brief
> **Definition**: A Feature Brief is a high-level, non-technical description of a software capability that focuses exclusively on user value, devoid of implementation details. It serves as the primary artifact for aligning stakeholders and engineering teams.

In Agile methodologies, this often takes the form of a **User Story**, but a Feature Brief can be broader, encompassing the strategic "North Star" of a module.

## 2. The "Why": Alignment and Value
Why do we write briefs instead of jumping straight to code?
1.  **Alignment**: Ensures the business (Client/boss) and the execution (Engineer) agree on the *destination* before discussing the *vehicle*.
2.  **Prevention of the "XY Problem"**: Users often ask for a solution (Y) to their problem (X), but their proposed solution is arguably wrong. A brief forces a return to X (the problem).
3.  **Scope Control**: strict briefs prevent "scope creep" by defining clear boundaries of value.

## 3. The "How": The Role-Feature-Benefit Model
To construct a rigoros feature brief, we employ the **Role-Feature-Benefit** model, popularized by **Mike Cohn** in his work on User Stories.

### The Standard Template
> "As a **[Role]**, I want **[Feature/Action]**, so that **[Benefit/Value]**."

1.  **Role**: Who is the specific actor? "User" is too vague. Use "Administrator", "Shopper", "Data Analyst".
2.  **Feature**: What is the action? Use domain verbs ("Purchase", "Filter", "Export"), not technical verbs ("Click", "Query", "Loop").
3.  **Benefit**: The critical component. If you cannot articulate the benefit, the feature should not exist.

### Implementation Steps
1.  **Draft the Raw Request**: Write down what the client asked for.
2.  **Extract the Actor**: Identify who is actually performing the work.
3.  **Interrogate the Value**: Ask "Why?" until you hit a business metric (Revenue, Time Saved, Risk Reduced).
4.  **Remove Mechanics**: Delete words like "database", "button", "screen", "Python", "script".
5.  **Synthesize**: Combine into the template.

## 4. Historical Context
*   **Kent Beck**: Extreme Programming (XP). Introduced the concept of "Stories" as a way to facilitate conversation rather than dictating detailed specifications upfront.
*   **Mike Cohn**: Solidified the standard `As a... I want... So that...` template in *User Stories Applied*.

## 5. Examples: From Mechanic to Architect

### Example 1: The Inventory System
**❌ The Mechanic (Bad)**
> "I need to write a Python script with a `for` loop that iterates over the CSV file and removes rows where `quantity` is zero."
*   *Critique*: Focuses on implementation (`for` loop, CSV). No business value stated.

**✅ The Architect (Good)**
> "As an **Inventory Manager**, I want to **automatically archive out-of-stock items**, so that **my active product list is not cluttered with unsellable goods**."
*   *Critique*: Clear actor. Clear value (decluttering). Implementation agnostic (could be SQL, Python, or manual).

### Example 2: The Login Screen
**❌ The Mechanic (Bad)**
> "Build a React component with two input fields and a submit button that hits the `/auth/login` endpoint."

**✅ The Architect (Good)**
> "As a **Security-Conscious User**, I want to **authenticate securely into the platform**, so that **my personal data remains private and protected**."

### Example 3: The "Wait Time"
**❌ The Mechanic (Bad)**
> "Use `time.sleep(5)` to wait between API calls so we don't get banned."

**✅ The Architect (Good)**
> "As a **System Administrator**, I want to **rate-limit outgoing requests**, so that **we maintain compliance with the external provider's Service Level Agreement (SLA)**."

## 6. The "So What?" Test
If your brief fails to convince a CEO, it is a failure.
*   **Engineer**: "I'm refactoring the backend."
*   **CEO**: "So what?"
*   **Engineer**: "So the code is cleaner."
*   **CEO**: "So what?"
*   **Engineer**: "So we can add new features 50% faster next quarter."
*   **CEO**: "Approved."

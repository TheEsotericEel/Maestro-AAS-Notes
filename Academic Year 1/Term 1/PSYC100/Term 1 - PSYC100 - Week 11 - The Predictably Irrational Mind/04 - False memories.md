# False Memories

> "Memory is a painter, not a photographer."

## 1. The Wikipedia Model of Memory
### What is it?
We intuitively think human memory is a **Read-Only Log** (like a video recording).
Science proves memory is a **Mutable Wiki Page**.
-   **The Process**: Every time you recall a memory, you pull it into RAM (Working Memory), edit it with your current emotions/knowledge, and then *save the edited version* back to the hard drive.
-   **Result**: The memory you have today is a copy of a copy of a copy.

## 2. The Misinformation Effect (Elizabeth Loftus)
### The experiment
-   **Setup**: Participants watched a car crash.
-   **Group A**: "How fast were the cars going when they **smashed**?"
-   **Group B**: "How fast were the cars going when they **hit**?"
-   **Result**: Group A estimated much higher speeds. Worse, weeks later, they "remembered" seeing broken glass. **There was no broken glass.**
-   **Leading Questions**: A single word ("Smashed") overwrote the source code of their memory.

## 3. Engineering Application: Incident Investigation
### The Unreliable Narrator
When a user (or dev) says "I definitely didn't change the config," they aren't necessarily lying. They might have a false memory.
-   **Rule 1**: **Logs > Memory**. If the logs say X and the human says Y, the human is wrong.
-   **Rule 2**: **Neutral Questions**.
    -   *Bad*: "Did you click the blue button?" (Plants the idea of blue).
    -   *Good*: "Walk me through exactly what you clicked."

## 4. Source Confusion
You recognize the face, but you forget *where* you saw it.
-   **Scenario**: You think a function is safe because you saw it in the documentation.
-   **Reality**: You saw it on StackOverflow in a "Don't do this" thread.
-   **Result**: You carry the *content* but lose the *metadata* (Source: Untrusted).

## ⚡ Key Takeaway
> **Human memory is lossy compression.**
> It prioritizes narrative coherence over factual accuracy. Never base a Root Cause Analysis solely on interviews.

# Selective Attention

> "The eye sees only what the mind is prepared to comprehend."

## 1. The Spotlight Effect (Simons & Chabris)
### The Invisible Gorilla
-   **Task**: "Count the basketball passes." (The Spotlight focuses on the Ball).
-   **Event**: A man in a full gorilla suit walks through the game, beats his chest, and leaves.
-   **Result**: **50% of people do not see the gorilla.**
-   **Inattentional Blindness**: We are blind to the obvious when our attention is committed elsewhere.

### The Single-Threaded Brain
Conscious attention is a single-threaded process. You cannot "multitask." You can only switch the spotlight rapidly (Context Switching).
-   **The Danger**: If you are looking for *Performance* bugs, you will be blind to *Security* bugs.

## 2. Engineering Application: Code Reviews
### The Checklist Protocol
Because you can't see everything at once, you must perform multiple passes with different filters.
1.  **Pass 1 (Logic)**: Does it do the right thing?
2.  **Pass 2 (Security)**: Is there an injection vulnerability?
3.  **Pass 3 (Style)**: Are the variable names correct?
*If you try to do all 3 at once, you will miss the Gorilla.*

## 3. Banner Blindness
Users learn to ignore parts of the screen that usually contain ads (Right rail, Top banner).
-   **UX Trap**: If you put a critical error message in the "Banner Blindness" zone, users will click past it and then complain the system broke "without warning."
-   **Fix**: Breaking the pattern. Popups (modals) force the spotlight to move.

## 4. The Cocktail Party Effect
The ability to filter out 100 voices to hear one.
-   **Mechanism**: The Reticular Activating System (RAS) acts as a gain filter.
-   **Trigger**: Your name. Or "Production Down."
-   **Focus**: Keep your signal-to-noise ratio high. If you alert on everything, you alert on nothing (Alert Fatigue).

## ⚡ Key Takeaway
> **Looking is not Seeing.**
> You only see what you are querying for. To find new bugs, you must update your query parameters.

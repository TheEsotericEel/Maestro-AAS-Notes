# Why We Lie to Ourselves

> "The hardest person to debug is yourself."

## 1. Cognitive Dissonance
### What is it?
The mental discomfort (psychological stress) experienced when a person holds two or more contradictory beliefs, ideas, or values, or performs an action that contradicts one of those beliefs.
-   **Leon Festinger (1957)**: The father of this theory.

### The Problem
The brain demands **Consistency**. When there is Dissonance (Inconsistency), the brain triggers a defense mechanism to resolve it.
-   **Belief**: "I am a smart, logical engineer."
-   **Action**: "I just spent 3 months building a feature nobody wants."
-   **Dissonance**: "Smart people don't build useless things. I built a useless thing. Therefore... I am not smart?" (PAIN).

### The Solution (Rationalization)
To stop the pain, the brain rewrites reality:
-   **Rationalization**: "The feature isn't useless. The users just don't understand it yet. It was a vital architectural experiment." (PAIN GONE).

## 2. The $1 vs $20 Experiment
### The Setup
Festinger asked students to do a mind-numbing task (turning pegs) for an hour, then paid them to lie to the next subject and say it was fun.
-   **Group A**: Paid $20 (High Reward).
-   **Group B**: Paid $1 (Low Reward).

### The Result
-   **Group A ($20)**: Admitted the task was boring. No dissonance. "I lied because I was paid $20." (External Justification).
-   **Group B ($1)**: **Claimed the task was actually fun.**
    -   *Logic*: "I'm not a liar. I wouldn't lie for a measly dollar. So, I must have actually enjoyed it." (Internal Justification).

## 3. Engineering Trap: The Sunk Cost Fallacy
Dissonance is the fuel for Sunk Cost.
1.  **Input**: You choose a tech sack (e.g., MongoDB) for a project that clearly needs SQL.
2.  **Conflict**: 6 months in, the data is a mess. Migrating is the logical choice.
3.  **Dissonance**: "If I switch now, I admit I made a mistake 6 months ago."
4.  **Rationalization**: "NoSQL is the future. We just need to optimize our queries. Switching is for quitters."
5.  **Result**: You double down on failure to protect your ego.

## 4. Forms of Self-Deception
| Form | Definition | Tech Example |
| :--- | :--- | :--- |
| **Effort Justification** | We value things more simply because we suffered for them. | "This framework is hard to learn, so it must be powerful." (Stockholm Syndrome). |
| **Confirmation Bias** | Seeking only information that supports your belief. | Reading only the "Pros" section of a library review after you've already installed it. |
| **Sour Grapes** | Devaluing what you couldn't achieve. | "I didn't get the Google job. Good, they're an evil corp anyway." |

## 🔍 Practical Examples
### Scenario: "It Works on My Machine"
-   **Fact**: The code broke production.
-   **Dissonance**: "I am a good coder" vs "I broke prod."
-   **Rationalization**: "It must be an Ops issue. The environment is wrong. My code is perfect."
-   **The Fix**: Accept the failure. "I missed an environment variable dependency. I will fix it."

## ⚡ Key Takeaway
> **Strong opinions, loosely held.**
> When the data contradicts your belief, change the belief, not the data.

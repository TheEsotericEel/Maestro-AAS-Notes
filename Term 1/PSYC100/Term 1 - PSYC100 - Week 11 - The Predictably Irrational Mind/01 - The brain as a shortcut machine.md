# The Brain as a Shortcut Machine

> "You are not a rational computer. You are a story-telling machine running on outdated software."

## 1. System 1 vs. System 2 (Kahneman)
You have two operating systems running in parallel.
-   **System 1 (Fast)**: Automatic, intuitive, emotional, effortless. (98% of uptime).
    -   *Tech*: A Regex matcher. Fast but prone to false positives.
-   **System 2 (Slow)**: Deliberate, logical, calculating, expensive. (2% of uptime).
    -   *Tech*: A deep learning model. Accurate but burns massive GPU (Glucose).

### The Cognitive Miser
The brain burns 20% of your calories. To save energy, it defaults to System 1. It uses **Heuristics** (Shortcuts) to make "good enough" decisions instantly.
-   **The Bug**: In the modern world (Code, Finance), "good enough" is often disastrously wrong. This systematic error is a **Bias**.

## 2. The Big Three Heuristics (Kahneman & Tversky, 1974)
### 1. Availability Heuristic
-   **Rule**: "If I can recall it easily, it must be likely."
-   **The Glitch**: We judge probability by *vividness*, not data.
-   **Tech Example**: "We need to optimize for a Server Fire." (Because AWS had a fire last year). Meanwhile, looking at logs (boring) shows we are losing 10x more money to SQL injection.

### 2. Representativeness Heuristic
-   **Rule**: "It looks like a duck, so it is a duck." (Stereotyping).
-   **The Glitch**: Ignoring Base Rates (Statistics).
-   **Tech Example**: "That library has a cool logo and 20k stars. It must be bug-free." (Ignoring the 500 open issues).

### 3. Anchoring Heuristic
-   **Rule**: "The first number I see is the truth."
-   **The Glitch**: FAiling to adjust sufficiently from an initial value.
-   **Tech Example**: "The estimate is 2 days." Now everyone is thinking 1-3 days. No one is thinking 20 days, even if 20 is right.

## 3. Engineering Application: Debugging Bias
When debugging, System 1 lies to you.
-   **Assumption**: "It's a network issue." (Because the network failed yesterday -> Availability).
-   **Fact**: It's a permissions issue.
-   **Protocol**: Force System 2. "What are the facts? What suggests it is *not* the network?"

## ⚡ Key Takeaway
> **Don't trust your gut on complex problems.**
> Your gut (System 1) is great for avoiding lions. It is terrible for distributed systems consensus algorithms.

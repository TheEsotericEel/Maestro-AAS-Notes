# Putting It All Together: The Debiasing Cockpit

> "The first principle is that you must not fool yourself—and you are the easiest person to fool." — Richard Feynman

## 1. The Interaction of Biases (The Crash)
Biases rarely happen in isolation. They stack like Swiss Cheese slices until a failure occurs.
-   **Scenario**: You are debugging a prod outage at 3 AM (Depleted).
-   **Availability**: "I remember a DB lock last month."
-   **Confirmation Bias**: You search logs *only* for DB locks.
-   **Sunk Cost**: You spend 3 hours diving down the DB rabbit hole.
-   **Result**: It was a Load Balancer issue. You lost 3 hours because your "Hot System" took over.

## 2. The Algorithm of Rationality (Pause-Probe-Reframe)
You cannot "cure" biases. You can only install "Error Handlers."

### Step 1: The Pause (Metacognition)
-   **Trigger**: High Stakes + High Emotion (or Speed).
-   **Action**: "I am about to make a decision > \$10k or > 1 week of work. STOP."

### Step 2: The Probe (Data)
-   **Question**: "What would I believe if I had never seen the Anchor?"
-   **Question**: "What implies my theory is *wrong*?" (Disconfirming Evidence).

### Step 3: The Reframe (Perspective)
-   **Technique**: **The Outsider Test**.
    -   *Ask*: "If I was fired, and a new CEO came in, what would they do?" (Zero-Based Thinking).

## 3. Practical Protocol: The Pre-Mortem (Klein/Kahneman)
Post-mortems explain why you died. Pre-mortems prevent death.
1.  **Time Travel**: "Assume it is 6 months from now. The project has failed spectacularly."
2.  **Generate Reasons**: "Why did it fail?"
    -   *Answers*: "We ignored the legacy debt." "The API didn't scale."
3.  **Prevention**: Fix those specific vulnerabilities *now*, before you start.
-   *Why it works*: It legitimize dissent and breaks Overconfidence / Optimism Bias.

## ⚡ Key Takeaway
> **Rationality is not a trait.**
> Rationality is a checklist.
> Use the checklist, or your caveman brain will pilot the spaceship into the sun.

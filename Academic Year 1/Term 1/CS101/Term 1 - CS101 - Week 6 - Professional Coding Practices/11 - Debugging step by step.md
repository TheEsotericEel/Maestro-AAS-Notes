# Lesson 11: Debugging Step by Step

## 1. The Core Philosophy
> "Debugging is twice as hard as writing the code in the first place. Therefore, if you write the code as cleverly as possible, you are, by definition, not smart enough to debug it." — *Brian Kernighan*

Debugging is not an art; it is an application of the **Scientific Method**.
1.  **Observe**: See the error.
2.  **Hypothesize**: "I think the loop is going one step too far."
3.  **Experiment**: Add a trace or write a test case.
4.  **Conclude**: proven or disproven.

## 2. The 5-Step Protocol (R.I.P.F.V.)
Professional Engineers do not "poke around" until it works. They follow a protocol.

1.  **Reproduce**: If you cannot make it fail on demand, you cannot fix it. Script the failure case.
2.  **Isolate**: Shrink the problem. If the app crashes, try to make just the function crash.
3.  **Pinpoint**: Use Binary Search (Code Tracing) to find the exact line of failure.
4.  **Fix**: Apply the correction.
5.  **Verify**: Run the reproduction script again to ensure the bug is dead.

## 3. Techniques

### The Wolf Fence Algorithm
Imagine a wolf (bug) is hiding in a forest (code).
1.  Build a fence down the middle (a print statement).
2.  Did the wolf howl on the left or right?
3.  Build a fence down the middle of *that* section.
4.  Repeat until the wolf is trapped in a 1x1m cage.

### Rubber Duck Debugging
Explain your code, line by line, to an inanimate object (or a patient colleague).
*   *Why it works*: Reading code silently uses a different part of the brain than speaking it. Articulating the logic often reveals the flaw ("...and then I iterate over the list... oh wait, the list is empty.").

## 4. Reading Tracebacks
The Traceback is the "Police Report". It tells you:
1.  **What** happened (`ZeroDivisionError`).
2.  **Where** it happened (`line 42`).
3.  **The Call Stack**: How we got there.

**Rule**: Read from the **bottom up**. The error is at the bottom. The cause is usually just above it.

## 5. Summary
Stop guessing. Stop changing random lines of code hoping it will compile. Be a detective.

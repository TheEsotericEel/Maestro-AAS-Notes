# Validation and Demonstration

## 1. The Demonstration Protocol

### What is it?
A Demo is not just "running code." It is a performance. You are demonstrating that the software meets requirements.

### The Script
Never "wing it." Prepare a script that covers 3 specific scenarios:
1.  **The Happy Path**: Input `10` -> Output `20`. (Shows basic functionality).
2.  **The Edge Case**: Input `0` -> Output `0`. (Shows logic boundaries).
3.  **The Error Case**: Input `"Hello"` -> Output `Error Message`. (Shows robustness).

---

## 2. The Confidence Check (Pre-flight)

Before showing your code to a human (Professor, Boss, Client), run the **10-Second Destruct Test**.
*   Smash the keyboard (Invalid characters).
*   Enter negative numbers.
*   Enter huge numbers.
*   Enter empty strings (Just hit Enter).

If your app crashes (Red Text), fix it. A crashing app is an automatic failure in professional environments.

---

## 3. Communicating Logic

When explaining your code:
*   **Don't say**: "Then I created a variable called x and used a f-string." (We can see that).
*   **Do say**: "We validate the input here to prevent negative prices, then apply the tax rate." (Explain the *Why*).

### Example Script
> "First, I'll demonstrate a standard transaction. I enter $100. You see the total is $110 with tax.
> Next, I'll test the validation. I enter -50. The system blocks it with a clear error message.
> Finally, I'll test text input. I type 'Ten'. The system handles the type error gracefully."

---

## 4. Truths
*   **"It works on my machine"** is not a valid excuse.
*   **Silent Failures** are worse than Crashes. (If I enter -50 and it prints "Total: $-55", you just lost money).
*   **The User is Chaos**. Design for them.

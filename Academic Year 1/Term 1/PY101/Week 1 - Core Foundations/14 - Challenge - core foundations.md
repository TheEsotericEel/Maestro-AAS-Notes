# Challenge: Core Foundations

## 🎯 The Job
You have been hired by "Python Café" to build their new Point of Sale (POS) system. Your first task is to create a **Receipt Generator** that accepts item details and prints a formatted, tax-calculated receipt.

## 🛠️ Requirements

### 1. Inputs (Data Ingest)
Ask the user for the following three pieces of information:
*   **Item Name**: (String) e.g., "Latte"
*   **Price**: (Float) e.g., 4.50
*   **Quantity**: (Integer) e.g., 2

### 2. Logic (Processing)
*   **Subtotal**: Calculate `price * quantity`.
*   **Tax**: Calculate 8% of the subtotal (`subtotal * 0.08`).
*   **Total**: Calculate `subtotal + tax`.

### 3. Output (Reporting)
Print a receipt exactly like the sample below.
*   **Separators**: Use `print("-" * 30)` for lines.
*   **Money**: All dollar attributes must be formatted to 2 decimal places (e.g., `$4.50`).

## 📝 Expected Output
```text
Item Name: Latte
Price: 4.50
Quantity: 2

--- Python Café Receipt ---
Item: Latte
Qty:  2
------------------------------
Subtotal: $9.00
Tax (8%): $0.72
Total:    $9.72
------------------------------
```

## 💡 Hints & Strategy
1.  **Casting**: Remember that `input()` returns a string. You **must** cast the price to `float` and the quantity to `int` immediately.
2.  **Constants**: Define `TAX_RATE = 0.08` at the top of your file. Magic numbers are professionally unacceptable.
3.  **Formatting**: Use `f"{variable:.2f}"` for all money values.

## 🧠 Self-Check (The "Code Review")
Before submitting, ask yourself:
*   [ ] Did I trap the user input correctly? (What if they type "two" instead of "2"? It will crash, and that's okay for now).
*   [ ] Are my variable names `snake_case`?
*   [ ] Is the tax calculation accurate?

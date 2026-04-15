# Lesson 03: Crafting Docstrings that Explain the Why

## 1. The Core Philosophy
Code tells you *how*. Comments tell you *why*. Docstrings tell you *how to use it*.

In Professional Software Engineering, a function without a docstring is a "black box" that requires the user to dismantle it (read the source code) to understand how to operate it. This violates the principle of **Encapsulation**.

## 2. The Contract (Design by Contract)
A well-written docstring defines a clear **contract** between the function (the supplier) and the caller (the client).
*   **Preconditions (Args)**: What the function requires to work correctly.
*   **Postconditions (Returns)**: What the function guarantees to provide in return.
*   **Side Effects**: Any changes to state outside the function (e.g., writing to a database).

## 3. The Google Style Guide
We adhere to the Google Python Style Guide for docstrings. It is the industry gold standard for readability.

### Structure
1.  **Summary Line**: A one-line imperative sentence describing the function (e.g., "Calculates user retention rate.").
2.  **Extended Description** (Optional): More detail on the algorithm or edge cases.
3.  **Args**: List of parameters, their types, and descriptions.
4.  **Returns**: Description of the return value and its type.
5.  **Raises**: List of exceptions the function might explicitly raise.

## 4. Practical Implementation

### The "Lazy" Docstring
```python
def send_email(user, subject, body):
    """Sends an email."""
    # ... implementation ...
```
*Critique*: This adds almost zero value. It repeats the function name. It fails to answer: What happens if the user has no email address? What if the network fails?

### The "Professional" Docstring
```python
def send_email(user: UserProfile, subject: str, message_body: str) -> bool:
    """Dispatches a transactional email to the specified user.

    Uses the default SMTP configuration defined in settings. If the user
    has opted out of notifications, this function will silently return False.

    Args:
        user: The UserProfile object containing the recipient's email using 'email_address' attribute.
        subject: The subject line of the email (max 78 chars).
        message_body: The raw text content of the email body.

    Returns:
        bool: True if the email was queued successfully, False if skipped due to
        user preferences or invalid email address.

    Raises:
        ConnectionError: If the SMTP server is unreachable.
    """
    # ... implementation ...
```

## 5. The "Help" Test
Python has a built-in mechanism to read these contracts: the `help()` function.
Run `help(your_function)` in the REPL.
*   **Visualizing the Output**: Does it look like a manual page?
*   **Completeness**: Can a developer use your function *without* seeing the code body?

## 6. Type Hinting vs. Docstrings
Modern Python uses **Type Hinting** (`user: UserProfile`) for strict validation, but Docstrings are still required for **context**.
*   **Type Hint**: Tells the linter "This must be a string".
*   **Docstring**: Tells the human "This string represents the ISO 8601 date".

## 7. Summary
A docstring is not an afterthought. It is the **specification** of your unit of work. Write the docstring *before* you write the code. This forces you to clarify your inputs and outputs before you get lost in the logic.

# Lesson 04: Writing Comments with Real Purpose

## 1. The Core Philosophy
> "Comments do not make up for bad code." — *Robert C. Martin (Uncle Bob)*

In professional environments, comments are often viewed with skepticism. Why? Because **code never lies, but comments often do**. When code changes, developers frequently forget to update the comments, turning them into "Zombie Comments"—misleading text that causes bugs.

**The Golden Rule**: Comments should explain **WHY** something is happening, not **WHAT** is happening.

## 2. Signal vs. Noise
Every line of text in a source file adds cognitive load. You must justify the existence of every comment.

### The "Echo" Comment (Noise)
These comments merely repeat what the code says. They clutter the screen.
```python
# Bad
i = i + 1  # Increment i
```
*Critique*: The code `i = i + 1` is already clear to any programmer. The comment adds 0% information.

### The "Insight" Comment (Signal)
These comments explain business logic, obscure bugs, or non-obvious decisions.
```python
# Good
# We add an epsilon (0.0001) to avoid divide-by-zero errors in edge cases
ratio = total / (count + 0.0001)
```
*Critique*: The code `+ 0.0001` looks weird on its own. The comment explains the *engineering reason* (mathematical stability).

## 3. When to Comment

### 1. Business Logic / Domain Rules
Explain *why* a specific arbitrary rule exists.
```python
# Users from 'Guest' tier are capped at 5 requests to prevent API abuse.
if user.tier == 'Guest' and request_count > 5:
    return False
```

### 2. Workarounds / Hacks
Sometimes, you cannot write perfect code (e.g., due to a library bug or legacy constraint). Admit it.
```python
# TODO(jdoe): The third-party 'pdf_lib' crashes on empty strings.
# We must pass a single space " " to prevent the crash.
pdf_lib.render(" ")
```

### 3. Complexity Warning
If an algorithm is inherently complex (e.g., regex), explain it.
```python
# Validates standard US phone numbers (e.g., (555) 123-4567 or 555-123-4567)
phone_regex = r"^\(?\d{3}\)?[-.\s]?\d{3}[-.\s]?\d{4}$"
```

## 4. The Refactoring Test
Before writing a comment to explain "messy" code, try to **refactor** the code to make the comment unnecessary.

**Before (Requires Explanation)**:
```python
# Check if user is eligible for senior discount (over 65 and member > 2 years)
if u.age > 65 and (d.today() - u.joined).days > 730:
    apply_discount()
```

**After (Self-Documenting)**:
```python
if user.is_eligible_for_senior_discount():
    apply_discount()
```
*Result*: The comment was replaced by a well-named function.

## 5. Summary
*   **Don't** use comments to explain bad variable names. Fix the names.
*   **Don't** use comments to apologize for bad code. Fix the code.
*   **Do** use comments to explain the *intent* behind the logic and the *reasons* for non-obvious decisions.

# Lesson 14: Validating Inputs Before They Break Things

## 1. The Core Philosophy
**Defensive Programming**: Assume that all input is malicious, malformed, or mistaken until proven otherwise.
Never allow "dirty" data to enter your "clean" logic.

## 2. The Pattern: Guard Clauses
Instead of verifying that data is *good* and entering a nested block, verify that data is *bad* and kicking it out. This keeps your "Happy Path" (the core logic) flat and readable.

### The "Arrow" Anti-Pattern
```python
def process_user(user):
    if user:
        if user.is_active:
            if user.has_permission:
                # Core Logic is buried 3 levels deep
                save_to_db(user)
```

### The Guard Clause Pattern
```python
def process_user(user):
    # Guard 1: Existence
    if not user:
        return
        
    # Guard 2: Status
    if not user.is_active:
        return
        
    # Guard 3: Authorization
    if not user.has_permission:
        return
        
    # Core Logic (Flat and Clean)
    save_to_db(user)
```

## 3. Data Sanitization
Validation is checking (Yes/No). Sanitization is cleaning (Fixing).
*   **Trimming**: `.strip()` whitespace from user strings.
*   **Casting**: Converting string "5" to integer `5`.

**Example**:
```python
def register_user(username: str):
    # Sanitize
    clean_name = username.strip().lower()
    
    # Validate
    if len(clean_name) < 3:
        raise ValueError("Username too short")
        
    # Process
    database.save(clean_name)
```

## 4. Layers of Defense
1.  **UI Layer**: HTML forms prevent empty submissions. (Can be bypassed).
2.  **API Layer**: Python code checks types and constraints. (Critical).
3.  **Database Layer**: SQL Constraints (`NOT NULL`, `UNIQUE`) ensure integrity even if code fails.

## 5. Summary
Your function is a fortress. The arguments are visitors. The Guard Clauses are the bouncers. Do not let anyone in without checking their ID.

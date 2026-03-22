# Lesson 02: Naming that tells a story

## 1. The Core Philosophy
> "There are only two hard things in Computer Science: cache invalidation and naming things." — *Phil Karlton*

Naming is not an artistic choice; it is a rigorous engineering decision. A name is the primary user interface of your code. If a variable, function, or class name requires the reader to look up its definition to understand its purpose, the name has failed.

## 2. Theoretical Framework
In Information Theory, code can be viewed as a transmission channel. Vague names introduce "noise," degrading the signal (intent).
*   **Signal**: The intent of the code (e.g., "Calculate the total revenue").
*   **Noise**: Ambiguity (e.g., `calc(d)`).

Your goal is to maximize the **Signal-to-Noise Ratio**.

## 3. The Rules of Engagement (PEP 8 & Beyond)

### The Standards
| Entity | Convention | Example |
| :--- | :--- | :--- |
| **Variables** | `snake_case` | `user_first_name`, `total_inventory_count` |
| **Functions** | `snake_case` | `calculate_total_tax()`, `validate_email_address()` |
| **Classes** | `PascalCase` | `UserProfile`, `InveventoryManager` |
| **Constants** | `SCREAMING_SNAKE` | `MAX_RETRY_ATTEMPTS`, `DEFAULT_TIMEOUT_SECONDS` |

### The "No-Mapping" Rule
The reader should never have to map a name to a concept in their head.
*   **Bad**: `l` (Reader maps `l` -> `list` -> `user list`)
*   **Good**: `active_user_list` (No mapping required)

## 4. Anti-Patterns to Avoid

### The "Generic" Trap
Generic names rob the code of context.
*   `data`: What data? User data? Sensor data?
*   `item`: A product? A structural node? An iterate?
*   `val` / `value`: The standard "I don't know what to name this" variable.

**Correction**:
```python
# Bad
for item in data:
    process(item)

# Good
for customer_order in pending_orders_queue:
    process_payment(customer_order)
```

### The "Hungarian Notation" Fallacy
In modern Python, encoding types in names (e.g., `strName`, `iCount`) is redundant and discouraged. The IDE and type hints handle this.
*   **Exceptions**: When the type *is* the core distinction (e.g., `user_id_str` vs `user_id_int` during a migration).

## 5. Practical Application: The "Telephone Test"
**Procedure**: Read your code aloud to a colleague without showing them the screen.
*   **Fail**: "Loop through `x` in `o` and add to `t`."
*   **Pass**: "Loop through `orders` in `order_list` and add to `total_revenue`."

## 6. Case Study

### The Obfuscated Code
```python
def c(d, r):
    t = 0
    for i in d:
        if i.s == 'a':
            t += i.p * r
    return t
```
*Critique*: This requires the reader to inspect the `i` object definition and the `c` function call to understand anything. It is impenetrable.

### The Professional Code
```python
def calculate_active_inventory_value(inventory_items, tax_rate):
    total_value = 0
    for item in inventory_items:
        if item.status == 'active':
            total_value += item.price * tax_rate
    return total_value
```
*Analysis*:
*   `c` -> `calculate_active_inventory_value`: Describes the *action* and the *result*.
*   `d` -> `inventory_items`: Describes the *content*.
*   `i.s` -> `item.status`: Describes the *attribute* clearly.

## 7. Summary
Treat names as labels on a complex dashboard. If the "Eject Pilot" button is labeled "Button 1", disaster is inevitable. Be explicit. Be verbose if necessary. Be clear.

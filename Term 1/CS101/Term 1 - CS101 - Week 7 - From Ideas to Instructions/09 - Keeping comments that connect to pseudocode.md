# Traceability and Documentation

## 1. Traceability in Engineering

### What is it?
Traceability is the ability to link a requirement (The Plan) to its specific implementation (The Code).

### Why does it matter?
Code rots. In 6 months, you will forget *why* you wrote that strict condition. **Anchor Comments** serve as breadcrumbs back to the original logical design.

---

## 2. The Anchor Comment System

Do not comment on *what* the code is doing (Syntax). Comment on *which part of the plan* this executes (Logic).

**Bad Commenting (Syntax Echo)**
```python
# Set x to 10
x = 10 
# Loop 5 times
for i in range(5):
    # Print i
    print(i)
```
*Critique*: This is useless noise. I can read Python; I know `x = 10` sets x to 10.

**Good Commenting (Logical Anchors)**
```python
# 1. Initialize Configuration
retry_count = 0
max_retries = 3

# 2. Attempt Connection Loop
while retry_count < max_retries:
    
    # 2.1 Check Network Status
    if is_connected():
        break
        
    # 2.2 Increment Retry Counter
    retry_count += 1
```
*Utility*: This tells me the *purpose* of the block.

---

## 3. Practical Examples

### Example: The Bridged Implementation

**The Plan**
1.  Get raw price.
2.  Validate price > 0.
3.  Calculate VAT (20%).
4.  Print Total.

**The Code**
```python
# 1. Get raw price
raw_price = input("Enter price: ")

# 2. Validate price > 0
# Note: Converting to float first to handle decimals
price = float(raw_price)
if price <= 0:
    print("Error: Price must be positive")
    exit()

# 3. Calculate VAT (20%)
vat = price * 0.20
total = price + vat

# 4. Print Total
print(f"Total: ${total:.2f}")
```

### The "Drift" Check
If you refactor the code (e.g., move VAT calculation to a function), **keep the comment**.
```python
# 3. Calculate VAT (20%)
total = calculate_gross_price(price)
```
The comment remains true: This line completes Step 3. The *implementation details* of Step 3 have just moved elsewhere.

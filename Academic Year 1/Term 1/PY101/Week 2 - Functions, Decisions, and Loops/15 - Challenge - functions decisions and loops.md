# Challenge - functions decisions and loops

## 🎯 Challenge Goal
Build a logic-driven "Order Processor" that filters items and calculates a final bill.

## 🛠️ Requirements
1.  **Function**: Create `calculate_tax(price)` that returns 8% of price.
2.  **Loop**: Iterate through a list of daily sales: `100, 40, 0, -5, 10`.
3.  **Logic**:
    - Skip 0 or negative values (`continue`).
    - Stop processing if a value matches `999` (Emergency Stop).
    - Accumulate valid sales into `total_sales`.
4.  **Count**: Track how many valid items were sold.
5.  **Output**: Print final count and total with tax.

## 📝 Expected Output
```text
Processing 100...
Processing 40...
Invalid value: 0
Invalid value: -5
Processing 10...

-- Report --
Valid Items: 3
Subtotal: $150.00
Tax: $12.00
Grand Total: $162.00
```

## 💡 Hints
- Initialize `total` and `count` to 0.
- Use `if price <= 0: continue`.
- Remember to add tax *after* the loop is done for the grand total.

## 🧠 Self-Check
- Did you define a function?
- Did loops skip the bad data?
- Are variables defined before the loop?

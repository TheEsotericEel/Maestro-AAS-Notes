# Challenge - basic data structures

## 🎯 Challenge Goal
Build an **Inventory Management System**.
You have a list of products (dictionaries). You need to filter them, update prices, and calculate the total value of stock.

## 🛠️ Requirements
1.  **Data**: Create a list called `inventory` with 3 dictionaries:
    - `{"name": "Laptop", "price": 1000, "stock": 5}`
    - `{"name": "Mouse", "price": 25, "stock": 10}`
    - `{"name": "Monitor", "price": 200, "stock": 0}`
2.  **Filter**: Create a new list `available` containing only items with `stock > 0`.
3.  **Update**: Apply a 10% discount to all items in `available` (update their price in place).
4.  **Calculate**: Sum up the total value (`price * stock`) of the `available` list.
5.  **Output**: Print the total value.

## 📝 Expected Output
```text
Processing Laptop...
Processing Mouse...
Total Inventory Value: $4725.0
```

## 💡 Hints
- Use a `for` loop to iterate.
- Use `if item["stock"] > 0:` to filter.
- Update syntax: `item["price"] = item["price"] * 0.9`.
- Accumulator pattern: `total += item["price"] * item["stock"]`.

## 🧠 Self-Check
- Did you modify the original dictionaries? (Check `inventory` at the end).
- Did you handle the item with 0 stock correcty?
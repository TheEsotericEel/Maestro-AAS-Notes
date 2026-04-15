# Dictionaries i - keys and values

## 🎯 End goal
- Create dictionaries using `{}`.
- Access values using `[key]`.
- Add and Update data.
- Understand **Key-Value Pairs**.

## 🧠 Core Concepts

### 1. The Mental Model: Labelled Jars
A List is a shelf of numbered boxes (0, 1, 2...).
A Dictionary is a shelf of **Labelled Jars**.
- **Key (Label)**: Unique identifier (e.g., "Name", "ID").
- **Value (Content)**: What's inside (e.g., "Alex", 123).

### 2. Syntax
- **Create**: `{ key : value, ... }`
- **Access**: `D[key]` (Lookup by label).

## 📝 Final shape

### Clean
```python
user = {
    "name": "Alex",
    "score": 10
}

print(user["name"])
user["score"] = 20
user["level"] = "Pro"
```

### Annotated
```python
user = {
    "name": "Alex",   # Key: "name", Value: "Alex"
    "score": 10
}

print(user["name"])   # Lookup "name" -> "Alex"
user["score"] = 20    # Update existing key
user["level"] = "Pro" # Create NEW key
```

## 🔄 Processes

### The Lookup
1.  **Code**: `user["name"]`
2.  **Search**: Python finds the label "name" instantly (hashing).
3.  **Result**: Returns contents ("Alex").

## ⚡ Associations
- `{}` → Index
- `Key` → Limit (Must be immutable, unique)
- `Value` → Anything
- `KeyError` → Label not found

## ⚠️ Traps
- **Duplicate Keys**: `{"a": 1, "a": 2}` keeps only the LAST one (`{"a": 2}`). (Labels must be unique).
- **Unhashable Keys**: You can't use a List as a Key. `{[1]: "bad"}` crashes.
- **Ordering**: (Prior to Python 3.7) Dicts were unordered. Now they remember insert order, but treat them as unordered maps mentally.

## 🔍 Truth lines
```text
d = {"a": 1}
d["a"] → 1
d["b"] → KeyError
d["b"] = 2
d → {"a": 1, "b": 2}
```

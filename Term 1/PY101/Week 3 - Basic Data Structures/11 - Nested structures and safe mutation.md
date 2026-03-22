# Nested structures and safe mutation

## 🎯 End goal
- Access data deep inside lists/dicts (`data[0]["name"]`).
- Mutate inner values.
- Handle missing keys safely with `.get()`.

## 🧠 Core Concepts

### 1. The Drill Down
- **Concept**: Data structures can hold other data structures.
- **Visualization**: A Box (List) containing Jars (Dicts).
- **Access**: Step-by-step. Open Box → Pick Jar → Read Label.

### 2. Safe Navigation
- **Problem**: `user["address"]["city"]` crashes if "address" is missing.
- **Solution**: `.get()`.
- **Chain**: `user.get("address", {}).get("city", "Unknown")`.

## 📝 Final shape

### Clean
```python
users = [
    {"id": 1, "name": "Alex", "meta": {"role": "admin"}},
    {"id": 2, "name": "Bob"}
]

# Drill down
role = users[0]["meta"]["role"]

# Safe access
role2 = users[1].get("meta", {}).get("role", "guest")
```

### Annotated
```python
users = [
    {"id": 1, "name": "Alex", "meta": {"role": "admin"}},
    {"id": 2, "name": "Bob"}
]

# 1. users[0] -> Gets first dict
# 2. ["meta"] -> Gets meta dict
# 3. ["role"] -> Gets "admin"
role = users[0]["meta"]["role"]

# Bob has no "meta".
# .get("meta", {}) returns empty dict {} if missing.
# .get("role", "guest") looks inside that empty dict.
role2 = users[1].get("meta", {}).get("role", "guest")
```

## 🔄 Processes

### The Path Trace
1.  Identify the structure: `List` of `Dicts`.
2.  Index the List: `[0]`
3.  Key the Dict: `["meta"]`
4.  Key the Inner Dict: `["role"]`

## ⚡ Associations
- `L[i][j]` → Grid / Matrix
- `D[k][k2]` → JSON-like structure
- `KeyError` → Path broken
- `.get(k, default)` → Safety net

## ⚠️ Traps
- **Copying Nested Data**: A shallow copy `x[:]` copies the *List*, but the *Dicts inside* are still shared. (The "Shared Jars" problem).
- **NoneType Error**: `d.get("missing")["child"]` crashes because `get` returned `None`, and `None` has no keys. Use `get("missing", {})`.

## 🔍 Truth lines
```text
matrix = [[1, 2], [3, 4]]
matrix[1][0] → 3

data = {"users": [{"name": "A"}]}
data["users"][0]["name"] → "A"
```

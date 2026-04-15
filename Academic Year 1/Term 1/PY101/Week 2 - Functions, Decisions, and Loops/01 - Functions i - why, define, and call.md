# Functions i - why, define, and call

## 🎯 End goal
- **Define** a function using `def`.
- **Call** a function using `()`.
- **Reuse** code to avoid repetition.
- Understand the **DRY** Principle: Don't Repeat Yourself.

## 🧠 Core Concepts

### 1. The Function Header
- **Syntax**: `def function_name():`
- **Parts**:
  - `def`: Keyword to start definition.
  - `name`: Snake_case name of action.
  - `()`: Parentheses (for parameters, later).
  - `:`: Colon starts the body.

### 2. The Body
- **Rule**: Must be **indented** (usually 4 spaces).
- **Behavior**: This code *does not run* when defined. It runs only when *called*.

### 3. The Call
- **Syntax**: `function_name()`
- **Action**: Jumps to the function, runs lines, jumps back.

## 📝 Final shape

### Clean
```python
def welcome_user():
    print("Welcome to the system.")
    print("Loading preferences...")

print("Start")
welcome_user()
print("End")
```

### Annotated
```python
# 1. Define the recipe (does not run yet)
def welcome_user():
    print("Welcome to the system.")
    print("Loading preferences...")

print("Start")      # 2. Runs first
welcome_user()      # 3. Jumps to line 2, runs body, returns here
print("End")        # 4. Runs last
```

## 🔄 Processes

### The "DRY" Refactor
1. **Spot Duplication**: See the same 3 lines of code in two places?
2. **Extract**: Create a function `def do_thing():` with those lines.
3. **Replace**: Delete the duplicate lines and write `do_thing()` instead.

## ⚡ Associations
- `def` → "Here is a recipe"
- `()` → "Do it now"
- Indentation → "This belongs to the function"

## ⚠️ Traps
- **Forgetting `()`**: `print(welcome_user)` prints `<function ...>` instead of running it.
- **IndentationErrors**: All lines in the body must line up exactly.
- **Defining After Call**: You must define `def foo():` *before* you call `foo()` in the script.

## 🔍 Truth lines
```text
def say_hi():
    print("Hi")
say_hi() → Hi
print(say_hi) → <function say_hi at ...>
```

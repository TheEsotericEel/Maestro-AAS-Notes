# Introduce the Stack

## 1. Introduction
A Stack is a fundamental data structure that follows the LIFO (Last In, First Out) principle. It's a collection where you can only add and remove items at one end - the top. This simple restriction makes stacks incredibly useful for many programming scenarios and mirrors many real-world behaviors.

## 2. The Pancake Stack Analogy
### Visualizing Stack Behavior
Imagine a brunch food truck making pancakes:

```
┌─────────────┐  ← Top (where we add/remove)
│   Pancake 3  │  ← Most recent
├─────────────┤
│   Pancake 2  │  
├─────────────┤
│   Pancake 1  │  ← First added
└─────────────┘  ← Bottom (never touched directly)
```

**The Process**:
1. Cook puts Pancake 1 on the plate
2. Cook puts Pancake 2 on top of Pancake 1
3. Cook puts Pancake 3 on top of Pancake 2
4. Customer takes Pancake 3 (from the top)
5. Next customer takes Pancake 2
6. Final customer takes Pancake 1

**Key Principle**: Pancakes are only added and removed from the top - never from the middle or bottom.

## 3. Formal Stack Definition
### Stack Characteristics
**"A Stack is a collection where you can only add and remove items at the top, following that last-in, first-out behavior."**

This means:
- **Single access point**: Only the top can be accessed
- **LIFO behavior**: Last item added is first item removed
- **Restricted operations**: No direct access to middle or bottom items

### Mathematical Representation
If items are pushed in order: A → B → C
They will be popped in order: C → B → A

## 4. Stack Operations
### Core Operations
```python
# Basic stack operations using Python list
stack = []

# Push (add to top)
stack.append("A")  # Stack: ["A"]
stack.append("B")  # Stack: ["A", "B"] 
stack.append("C")  # Stack: ["A", "B", "C"]

# Pop (remove from top)
top_item = stack.pop()  # Returns "C", Stack: ["A", "B"]

# Peek (look at top without removing)
top_item = stack[-1]    # Returns "B", Stack unchanged: ["A", "B"]
```

### Operation Summary
| Operation | Description | Python Method | Time Complexity |
|-----------|-------------|---------------|-----------------|
| Push | Add item to top | `append()` | O(1) |
| Pop | Remove and return top | `pop()` | O(1) |
| Peek | Look at top without removing | `stack[-1]` | O(1) |
| Is Empty | Check if stack has items | `len(stack) == 0` | O(1) |
| Size | Get number of items | `len(stack)` | O(1) |

## 5. Stack Visualization
### Step-by-Step Example
```python
# Visual representation of stack operations
stack = []

print("Initial:", stack)        # []

# Step 1: Push first item
stack.append("plate 1")
print("After push 1:", stack)  # ["plate 1"]

# Step 2: Push second item  
stack.append("plate 2")
print("After push 2:", stack)  # ["plate 1", "plate 2"]

# Step 3: Push third item
stack.append("plate 3")
print("After push 3:", stack)  # ["plate 1", "plate 2", "plate 3"]

# Step 4: Pop top item
top_plate = stack.pop()
print("Popped:", top_plate)    # "plate 3"
print("After pop:", stack)     # ["plate 1", "plate 2"]

# Step 5: Pop another item
top_plate = stack.pop()
print("Popped:", top_plate)    # "plate 2"
print("After pop:", stack)     # ["plate 1"]
```

### Visual Stack Representation
```
State after pushing "plate 1", "plate 2", "plate 3":

Top ↑
┌─────────────┐
│   plate 3   │  ← Current top
├─────────────┤
│   plate 2   │
├─────────────┤
│   plate 1   │
└─────────────┘
```

## 6. Real-World Stack Examples
### Example 1: Pile of Plates
```python
# Cafeteria plate stack
plate_stack = []

# Add plates as they're cleaned
plate_stack.append("blue plate")
plate_stack.append("red plate") 
plate_stack.append("green plate")

# Take plates for serving
plate = plate_stack.pop()  # Takes "green plate" (last added)
print(f"Serving on: {plate}")

# Next serving
plate = plate_stack.pop()  # Takes "red plate"
print(f"Serving on: {plate}")
```

### Example 2: Browser History
```python
# Browser back button behavior
page_history = []

# User visits pages
page_history.append("homepage")
page_history.append("products") 
page_history.append("checkout")
page_history.append("confirmation")

# User presses back button
current_page = page_history.pop()  # Goes back to "checkout"
print(f"Back to: {current_page}")

# Presses back again
current_page = page_history.pop()  # Goes back to "products"
print(f"Back to: {current_page}")
```

### Example 3: Function Call Stack
```python
def function_c():
    print("Function C running")
    return "C result"

def function_b():
    print("Function B starts")
    result = function_c()
    print("Function B ends")
    return result

def function_a():
    print("Function A starts") 
    result = function_b()
    print("Function A ends")
    return result

# Call stack visualization:
# A calls B, B calls C
# C returns first, then B, then A (LIFO)
result = function_a()
```

## 7. Stack Implementation
### Basic Stack Class
```python
class Stack:
    """A simple Stack implementation using Python list"""
    
    def __init__(self):
        """Initialize empty stack"""
        self.items = []
    
    def push(self, item):
        """Add item to top of stack"""
        self.items.append(item)
        print(f"Pushed: {item}")
    
    def pop(self):
        """Remove and return top item"""
        if self.is_empty():
            raise IndexError("Cannot pop from empty stack")
        
        item = self.items.pop()
        print(f"Popped: {item}")
        return item
    
    def peek(self):
        """Look at top item without removing"""
        if self.is_empty():
            raise IndexError("Cannot peek empty stack")
        
        return self.items[-1]
    
    def is_empty(self):
        """Check if stack is empty"""
        return len(self.items) == 0
    
    def size(self):
        """Get number of items in stack"""
        return len(self.items)
    
    def __str__(self):
        """String representation of stack"""
        return f"Stack: {self.items}"

# Usage example
stack = Stack()
stack.push("A")
stack.push("B")
stack.push("C")

print(f"Top item: {stack.peek()}")  # "C"
print(f"Stack size: {stack.size()}")  # 3

stack.pop()  # Removes "C"
stack.pop()  # Removes "B"
stack.pop()  # Removes "A"

print(f"Is empty: {stack.is_empty()}")  # True
```

### Enhanced Stack with Error Handling
```python
class SafeStack:
    """Stack with comprehensive error handling"""
    
    def __init__(self, name="Stack"):
        self.items = []
        self.name = name
    
    def push(self, item):
        """Safely push item to stack"""
        self.items.append(item)
        print(f"{self.name}: Pushed {item}")
    
    def pop(self):
        """Safely pop item from stack"""
        if self.is_empty():
            print(f"{self.name}: Warning - Cannot pop from empty stack")
            return None
        
        item = self.items.pop()
        print(f"{self.name}: Popped {item}")
        return item
    
    def peek(self):
        """Safely peek at top item"""
        if self.is_empty():
            print(f"{self.name}: Warning - Cannot peek empty stack")
            return None
        
        return self.items[-1]
    
    def is_empty(self):
        """Check if stack is empty"""
        return len(self.items) == 0
    
    def clear(self):
        """Remove all items from stack"""
        self.items.clear()
        print(f"{self.name}: Stack cleared")

# Usage
safe_stack = SafeStack("Plate Stack")
safe_stack.push("plate 1")
safe_stack.push("plate 2")

safe_stack.pop()
safe_stack.pop()
safe_stack.pop()  # Warning message
```

## 8. Common Stack Applications
### Application 1: Text Editor Undo
```python
class TextEditor:
    """Simple text editor with undo functionality"""
    
    def __init__(self):
        self.content = ""
        self.undo_stack = Stack()
    
    def type_text(self, text):
        """Add text and save state for undo"""
        self.undo_stack.push(self.content)
        self.content += text
        print(f"Typed: '{text}'")
    
    def undo(self):
        """Undo last typing action"""
        if not self.undo_stack.is_empty():
            self.content = self.undo_stack.pop()
            print("Undo successful")
        else:
            print("Nothing to undo")
    
    def get_content(self):
        """Get current content"""
        return self.content

# Usage
editor = TextEditor()
editor.type_text("Hello ")
editor.type_text("World!")
print(f"Content: {editor.get_content()}")  # "Hello World!"

editor.undo()
print(f"After undo: {editor.get_content()}")  # "Hello "

editor.undo()
print(f"After undo: {editor.get_content()}")  # ""
```

### Application 2: Parentheses Matching
```python
def check_balanced_brackets(expression):
    """Check if brackets are balanced using stack"""
    stack = Stack()
    opening_brackets = "({["
    closing_brackets = ")}]"
    bracket_pairs = {')': '(', '}': '{', ']': '['}
    
    for char in expression:
        if char in opening_brackets:
            stack.push(char)
        elif char in closing_brackets:
            if stack.is_empty():
                return False
            
            top = stack.pop()
            if bracket_pairs[char] != top:
                return False
    
    return stack.is_empty()

# Test cases
expressions = [
    "({[]})",      # True
    "({[})",       # False  
    "((()))",      # True
    "(()",         # False
    "([]){}",      # True
]

for expr in expressions:
    result = check_balanced_brackets(expr)
    print(f"{expr}: {result}")
```

### Application 3: Base Conversion
```python
def decimal_to_binary(decimal_num):
    """Convert decimal number to binary using stack"""
    if decimal_num == 0:
        return "0"
    
    stack = Stack()
    num = decimal_num
    
    # Push remainders onto stack
    while num > 0:
        remainder = num % 2
        stack.push(str(remainder))
        num = num // 2
    
    # Pop to build binary string
    binary = ""
    while not stack.is_empty():
        binary += stack.pop()
    
    return binary

# Usage
numbers = [0, 1, 2, 5, 10, 15, 255]
for num in numbers:
    binary = decimal_to_binary(num)
    print(f"{num} in binary: {binary}")
```

## 9. Identifying Stack Behavior
### Stack vs Non-Stack Examples
```python
# Stack behavior - only top access
def stack_behavior():
    """Example of proper stack usage"""
    stack = []
    
    # Only push to top
    stack.append("item 1")
    stack.append("item 2")
    stack.append("item 3")
    
    # Only pop from top
    while stack:
        item = stack.pop()
        print(f"Removed: {item}")

# Non-stack behavior - random access
def non_stack_behavior():
    """Example that violates stack principles"""
    items = ["A", "B", "C", "D"]
    
    # This is NOT stack behavior:
    items.remove("B")      # Removing from middle
    items.insert(1, "X")    # Inserting in middle
    items[0] = "Y"         # Direct access to any position
```

### Quiz: Stack or Not Stack?
```python
# Which of these follow stack behavior?

# 1. Browser back button - YES (stack)
# 2. Printer queue - NO (FIFO)
# 3. Undo/Redo system - YES (stack)
# 4. People in elevator line - NO (FIFO)
# 5. Pancake stack - YES (stack)
# 6. Bookshelf with random access - NO (not restricted)
```

## 10. Performance Analysis
### Time Complexity
| Operation | Best Case | Average Case | Worst Case |
|-----------|-----------|-------------|------------|
| Push | O(1) | O(1) | O(1) |
| Pop | O(1) | O(1) | O(1) |
| Peek | O(1) | O(1) | O(1) |
| Search | O(n) | O(n) | O(n) |

### Space Complexity
- **Space**: O(n) where n is number of items
- **Auxiliary Space**: O(1) for basic operations

### Advantages of Stacks
- **Simple implementation**: Easy to understand and code
- **Fast operations**: All basic operations are O(1)
- **Memory efficient**: No wasted space
- **Predictable behavior**: Always LIFO
- **Wide applicability**: Many real-world scenarios

### Limitations of Stacks
- **Restricted access**: Can only access top item
- **No random access**: Cannot directly access middle items
- **Fixed behavior**: Always LIFO, cannot be FIFO
- **Search inefficiency**: Must pop all items to find specific one

## 11. Quick Checks
- What is a Stack? → Collection where you only add/remove at the top
- What principle does Stack follow? → LIFO (Last In, First Out)
- How do you add to a Stack? → Push operation (append in Python)
- How do you remove from a Stack? → Pop operation (pop in Python)
- Is browser Back button a Stack? → Yes, most recent page undone first
- Can you access middle items directly in a Stack? → No, only the top

## 12. Summary
A Stack is a fundamental data structure with strict access rules:

### Core Concept
- **Single access point**: Only the top can be accessed
- **LIFO behavior**: Last item added is first item removed
- **Restricted operations**: No direct access to middle or bottom items

### Key Operations
- **Push**: Add item to top
- **Pop**: Remove and return top item
- **Peek**: Look at top item without removing
- **Is Empty**: Check if stack has items

### Real-World Applications
- **Browser history**: Back button undoes most recent visit
- **Text editing**: Undo reverses most recent change
- **Function calls**: Last function called returns first
- **Plate/pancake stacks**: Only top item is accessible

### Implementation in Python
- **Natural fit**: Python lists with `append()` and `pop()`
- **Custom classes**: Can encapsulate stack behavior
- **Error handling**: Important for empty stack operations

> **Key Insight**: "A Stack is like a pile of anything - plates, pancakes, papers - where you can only work with the top item. This simple restriction makes it incredibly powerful for managing order and state in programming."

### Mastery Checklist
- ✅ Define Stack in simple terms
- ✅ Explain LIFO behavior
- ✅ Identify real-world Stack examples
- ✅ Implement Stack using Python lists
- ✅ Create custom Stack class
- ✅ Apply Stack to practical problems
- ✅ Distinguish Stack from non-Stack behavior
- ✅ Understand Stack performance characteristics
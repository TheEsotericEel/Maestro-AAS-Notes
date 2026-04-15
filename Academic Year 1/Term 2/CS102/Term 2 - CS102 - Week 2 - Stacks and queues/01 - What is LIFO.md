# What is LIFO?

## 1. Introduction
LIFO stands for "Last In, First Out" - a fundamental principle in computer science where the last item added to a collection is the first one to be removed. This concept is the foundation of stack data structures and appears in many real-world systems and programming patterns.

## 2. The Cafeteria Tray Analogy
### Visualizing LIFO
Imagine a cafeteria with a stack of trays:

```
┌─────────────┐  ← Top of stack (most recent)
│    Tray C    │
├─────────────┤
│    Tray B    │
├─────────────┤
│    Tray A    │  ← Bottom of stack (oldest)
└─────────────┘
```

**The Process**:
1. Worker puts Tray A on the stack
2. Worker puts Tray B on top of Tray A
3. Worker puts Tray C on top of Tray B
4. Customer takes Tray C (the last one added)
5. Next customer takes Tray B
6. Final customer takes Tray A

**Key Principle**: The last tray that was put on the stack is the first tray that gets taken off.

## 3. Formal Definition
### LIFO Rule
**"In LIFO, the last item that goes in is the first item that comes out."**

This means:
- **Last In** = Most recently added item
- **First Out** = First item to be removed
- **Order is reversed** when removing items

### Mathematical Representation
If items are added in order: A → B → C → D
They will be removed in order: D → C → B → A

## 4. Real-World LIFO Examples
### Example 1: Browser History
```python
# Browser navigation follows LIFO
# User visits pages: A → B → C
# Pressing Back button: C → B → A

pages_visited = ["homepage", "products", "checkout"]
# Last page visited = "checkout"
# First page to go back to = "checkout"
```

### Example 2: Text Editor Undo
```python
# User makes changes: type sentence → add formatting → insert image
# Undo sequence: remove image → remove formatting → delete sentence
undo_stack = ["typed sentence", "added formatting", "inserted image"]
# Most recent change (image) gets undone first
```

### Example 3: Stack of Plates
```python
# Plates stacked: bottom → middle → top
# Removal order: top → middle → bottom
plate_stack = ["plate_bottom", "plate_middle", "plate_top"]
# Top plate (last added) gets taken first
```

## 5. Non-LIFO Examples
### Example: Elevator Behavior
People entering and leaving an elevator typically follow FIFO (First In, First Out):
- First person in often stands near the door
- First person in typically exits first
- This is NOT LIFO behavior

### Example: Queue/Line
People waiting in line:
- First person to arrive gets served first
- This follows FIFO, not LIFO

## 6. LIFO in Python
### Basic Implementation
Python lists naturally support LIFO behavior using `append()` and `pop()`:

```python
# LIFO stack using Python list
stack = []

# Add items (push operation)
stack.append("A")  # Stack: ["A"]
stack.append("B")  # Stack: ["A", "B"]
stack.append("C")  # Stack: ["A", "B", "C"]

# Remove items (pop operation)
item1 = stack.pop()  # Returns "C", Stack: ["A", "B"]
item2 = stack.pop()  # Returns "B", Stack: ["A"]
item3 = stack.pop()  # Returns "A", Stack: []

print(f"Removed in order: {item1}, {item2}, {item3}")
# Output: Removed in order: C, B, A
```

### Step-by-Step Visualization
```python
# Step 1: Start with empty stack
stack = []  # []

# Step 2: Add first item
stack.append("A")  # ["A"]

# Step 3: Add second item  
stack.append("B")  # ["A", "B"]

# Step 4: Add third item
stack.append("C")  # ["A", "B", "C"]

# Step 5: Remove top item
removed = stack.pop()  # Returns "C", stack becomes ["A", "B"]

# Step 6: Remove next item
removed = stack.pop()  # Returns "B", stack becomes ["A"]

# Step 7: Remove final item
removed = stack.pop()  # Returns "A", stack becomes []
```

## 7. Practical Applications
### Application 1: Function Call Stack
```python
def function_a():
    print("A starts")
    function_b()
    print("A ends")

def function_b():
    print("B starts")
    function_c()
    print("B ends")

def function_c():
    print("C runs")

# Call stack follows LIFO
# A calls B, B calls C
# C returns first (last called), then B, then A
function_a()
```

### Application 2: Expression Evaluation
```python
# Evaluating mathematical expressions using stack
def evaluate_expression(expr):
    stack = []
    
    for char in expr:
        if char.isdigit():
            stack.append(char)
        elif char == '+':
            b = stack.pop()  # Second operand
            a = stack.pop()  # First operand
            result = int(a) + int(b)
            stack.append(str(result))
    
    return stack.pop() if stack else 0

# Simple evaluation: "23+" means 2 + 3 = 5
result = evaluate_expression("23+")
print(f"Result: {result}")  # Result: 5
```

### Application 3: Undo/Redo System
```python
class TextEditor:
    def __init__(self):
        self.content = ""
        self.undo_stack = []
        self.redo_stack = []
    
    def type_text(self, text):
        self.undo_stack.append(self.content)
        self.content += text
        self.redo_stack.clear()  # Clear redo stack on new action
    
    def undo(self):
        if self.undo_stack:
            self.redo_stack.append(self.content)
            self.content = self.undo_stack.pop()
    
    def redo(self):
        if self.redo_stack:
            self.undo_stack.append(self.content)
            self.content = self.redo_stack.pop()

# Usage
editor = TextEditor()
editor.type_text("Hello ")
editor.type_text("World!")
print(editor.content)  # "Hello World!"

editor.undo()
print(editor.content)  # "Hello "

editor.undo()
print(editor.content)  # ""

editor.redo()
print(editor.content)  # "Hello "
```

## 8. Common LIFO Patterns
### Pattern 1: Stack Operations
```python
# Standard stack operations
class Stack:
    def __init__(self):
        self.items = []
    
    def push(self, item):
        """Add item to top of stack"""
        self.items.append(item)
    
    def pop(self):
        """Remove and return top item"""
        if not self.is_empty():
            return self.items.pop()
        raise IndexError("Stack is empty")
    
    def peek(self):
        """Look at top item without removing"""
        if not self.is_empty():
            return self.items[-1]
        raise IndexError("Stack is empty")
    
    def is_empty(self):
        """Check if stack is empty"""
        return len(self.items) == 0
    
    def size(self):
        """Get number of items in stack"""
        return len(self.items)

# Usage
stack = Stack()
stack.push("A")
stack.push("B")
stack.push("C")

print(f"Top item: {stack.peek()}")  # "C"
print(f"Stack size: {stack.size()}")  # 3

while not stack.is_empty():
    item = stack.pop()
    print(f"Popped: {item}")
# Output: Popped: C, Popped: B, Popped: A
```

### Pattern 2: Parentheses Matching
```python
def check_balanced_parentheses(expression):
    """Check if parentheses are balanced using stack"""
    stack = []
    pairs = {'(': ')', '[': ']', '{': '}'}
    
    for char in expression:
        if char in pairs.keys():  # Opening bracket
            stack.append(char)
        elif char in pairs.values():  # Closing bracket
            if not stack:
                return False
            
            opening = stack.pop()
            if pairs[opening] != char:
                return False
    
    return len(stack) == 0

# Test cases
print(check_balanced_parentheses("({[]})"))  # True
print(check_balanced_parentheses("({[})"))   # False
print(check_balanced_parentheses("((()))"))  # True
print(check_balanced_parentheses("(()"))     # False
```

## 9. Performance Characteristics
### Time Complexity
- **Push (add)**: O(1) - Constant time
- **Pop (remove)**: O(1) - Constant time  
- **Peek (look)**: O(1) - Constant time
- **Search**: O(n) - Linear time (must check all items)

### Space Complexity
- **Space**: O(n) - Proportional to number of items stored

### Advantages
- **Simple implementation**: Easy to understand and use
- **Fast operations**: All basic operations are constant time
- **Memory efficient**: No wasted space
- **Natural fit**: Perfect for many real-world scenarios

### Limitations
- **Limited access**: Can only access top item directly
- **No random access**: Cannot access middle items efficiently
- **Fixed behavior**: Always follows LIFO, cannot change to FIFO

## 10. Quick Checks
- What does LIFO stand for? → Last In, First Out
- Which item gets removed first in LIFO? → The most recently added one
- What Python methods implement LIFO? → `append()` for adding, `pop()` for removing
- Is browser Back button LIFO? → Yes, most recent page first
- Is people waiting in line LIFO? → No, that's FIFO

## 11. Summary
LIFO (Last In, First Out) is a fundamental data structure principle:

### Core Concept
- **Last item added** is **first item removed**
- **Order reversal** when accessing items
- **Stack behavior** in real-world and programming contexts

### Key Characteristics
- **Simple and intuitive**: Mirrors many real-world scenarios
- **Efficient operations**: All basic operations are O(1)
- **Wide applications**: From browser history to function calls
- **Natural fit**: Perfect for undo/redo, navigation, and parsing

### Real-World Connections
- **Cafeteria trays**: Last tray on top taken first
- **Browser history**: Most recent page visited undone first
- **Text editing**: Last change made undone first
- **Function calls**: Last function called returns first

### Programming Implementation
- **Python lists**: `append()` + `pop()` create natural LIFO behavior
- **Stack class**: Encapsulates stack operations with clear interface
- **Algorithm applications**: Essential for parsing, evaluation, and backtracking

> **Key Insight**: "LIFO is nature's way of handling things - think of a stack of anything, and you'll naturally grab from the top. This simple principle powers everything from your browser's Back button to complex algorithms."

### Mastery Checklist
- ✅ Define LIFO in simple terms
- ✅ Identify real-world LIFO examples
- ✅ Distinguish LIFO from FIFO behaviors
- ✅ Implement LIFO using Python lists
- ✅ Understand stack operations (push, pop, peek)
- ✅ Apply LIFO to practical problems
- ✅ Recognize when LIFO is appropriate
- ✅ Implement basic stack data structure
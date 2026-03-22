# Stack Operations: Push and Pop

## 1. Introduction
Push and pop are the two fundamental operations that define a stack's behavior. Push adds an item to the top of the stack, while pop removes and returns the top item. These operations work together to maintain the LIFO (Last In, First Out) principle that makes stacks so useful in programming.

## 2. The Plate Stack Analogy
### Visualizing Push and Pop
Imagine a stack of plates in your kitchen:

```
Initial State:
┌─────────────┐
│             │  ← Empty stack
└─────────────┘

After Push "plate1":
┌─────────────┐  ← Top
│   plate1    │
└─────────────┘

After Push "plate2":
┌─────────────┐  ← Top
│   plate2    │
├─────────────┤
│   plate1    │
└─────────────┘

After Pop:
┌─────────────┐  ← Top
│   plate1    │
└─────────────┘
```

**The Process**:
1. **Push**: Add new plate on top of existing plates
2. **Pop**: Remove the top plate (most recently added)
3. **LIFO**: Last plate added is first plate removed

## 3. Push Operation
### Definition and Purpose
**Push** adds an item to the top of the stack. In Python lists, this is implemented using `append()`.

### Basic Push Implementation
```python
# Basic push operation
stack = []

# Push first item
stack.append("plate1")
print(f"After push 1: {stack}")  # ["plate1"]

# Push second item
stack.append("plate2")
print(f"After push 2: {stack}")  # ["plate1", "plate2"]

# Push third item
stack.append("plate3")
print(f"After push 3: {stack}")  # ["plate1", "plate2", "plate3"]
```

### Push Operation Details
```python
def push(stack, item):
    """Push an item onto the stack"""
    stack.append(item)
    print(f"Pushed: {item}")
    print(f"Stack is now: {stack}")

# Usage
my_stack = []
push(my_stack, "A")  # Pushed: A, Stack is now: ['A']
push(my_stack, "B")  # Pushed: B, Stack is now: ['A', 'B']
push(my_stack, "C")  # Pushed: C, Stack is now: ['A', 'B', 'C']
```

### Visual Push Process
```python
# Step-by-step visualization of push operations
stack = []

print("Step 1: Empty stack")
print(f"Stack: {stack}")
print("Top: None")

print("\nStep 2: Push 'plate1'")
stack.append("plate1")
print(f"Stack: {stack}")
print(f"Top: {stack[-1]}")  # 'plate1'

print("\nStep 3: Push 'plate2'")
stack.append("plate2")
print(f"Stack: {stack}")
print(f"Top: {stack[-1]}")  # 'plate2'

print("\nStep 4: Push 'plate3'")
stack.append("plate3")
print(f"Stack: {stack}")
print(f"Top: {stack[-1]}")  # 'plate3'
```

## 4. Pop Operation
### Definition and Purpose
**Pop** removes and returns the top item from the stack. In Python lists, this is implemented using `pop()`.

### Basic Pop Implementation
```python
# Basic pop operation
stack = ["plate1", "plate2", "plate3"]
print(f"Initial stack: {stack}")

# Pop top item
top_plate = stack.pop()
print(f"Popped: {top_plate}")  # "plate3"
print(f"After pop: {stack}")   # ["plate1", "plate2"]

# Pop another item
top_plate = stack.pop()
print(f"Popped: {top_plate}")  # "plate2"
print(f"After pop: {stack}")   # ["plate1"]
```

### Pop Operation Details
```python
def pop_operation(stack):
    """Pop an item from the stack"""
    if not stack:
        print("Cannot pop from empty stack")
        return None
    
    item = stack.pop()
    print(f"Popped: {item}")
    print(f"Stack is now: {stack}")
    return item

# Usage
my_stack = ["A", "B", "C"]
pop_operation(my_stack)  # Popped: C, Stack is now: ['A', 'B']
pop_operation(my_stack)  # Popped: B, Stack is now: ['A']
pop_operation(my_stack)  # Popped: A, Stack is now: []
pop_operation(my_stack)  # Cannot pop from empty stack
```

### Visual Pop Process
```python
# Step-by-step visualization of pop operations
stack = ["plate1", "plate2", "plate3"]

print("Step 1: Initial stack")
print(f"Stack: {stack}")
print(f"Top: {stack[-1]}")  # 'plate3'

print("\nStep 2: Pop top item")
popped = stack.pop()
print(f"Popped: {popped}")  # 'plate3'
print(f"Stack: {stack}")
print(f"Top: {stack[-1]}")  # 'plate2'

print("\nStep 3: Pop another item")
popped = stack.pop()
print(f"Popped: {popped}")  # 'plate2'
print(f"Stack: {stack}")
print(f"Top: {stack[-1]}")  # 'plate1'
```

## 5. Combined Push and Pop Operations
### Push-Pop Sequence Example
```python
# Complete push-pop sequence
stack = []

print("=== Push Phase ===")
stack.append("Iron Man")
print(f"Pushed Iron Man: {stack}")

stack.append("Thor")
print(f"Pushed Thor: {stack}")

stack.append("Hulk")
print(f"Pushed Hulk: {stack}")

print("\n=== Pop Phase ===")
last_hero = stack.pop()
print(f"Popped: {last_hero}")
print(f"Remaining: {stack}")

last_hero = stack.pop()
print(f"Popped: {last_hero}")
print(f"Remaining: {stack}")

last_hero = stack.pop()
print(f"Popped: {last_hero}")
print(f"Remaining: {stack}")
```

### Interactive Stack Demo
```python
class InteractiveStack:
    """Interactive stack demonstration"""
    
    def __init__(self):
        self.items = []
    
    def push(self, item):
        """Push item onto stack"""
        self.items.append(item)
        self.display_stack(f"Pushed {item}")
    
    def pop(self):
        """Pop item from stack"""
        if not self.items:
            print("Stack is empty - cannot pop")
            return None
        
        item = self.items.pop()
        self.display_stack(f"Popped {item}")
        return item
    
    def display_stack(self, action):
        """Display current stack state"""
        print(f"{action}")
        print(f"Stack: {self.items}")
        if self.items:
            print(f"Top: {self.items[-1]}")
        else:
            print("Top: None")
        print("-" * 30)

# Usage demonstration
demo = InteractiveStack()
demo.push("plate1")
demo.push("plate2")
demo.push("plate3")
demo.pop()
demo.pop()
demo.pop()
```

## 6. Stack Top Access
### Accessing the Top Element
The top of the stack is always the last element in the Python list:

```python
stack = ["a", "b", "c"]

# Different ways to access top
top1 = stack[-1]      # Most common - last element
top2 = stack[len(stack)-1]  # Using length
top3 = stack[-1:]     # As sublist (returns ['c'])

print(f"Top (stack[-1]): {top1}")      # "c"
print(f"Top (len-1): {top2}")          # "c"
print(f"Top (slice): {top3}")          # ['c']
```

### Why Use stack[-1]?
```python
# Advantages of stack[-1] for top access
stack = ["item1", "item2", "item3"]

# Always works regardless of stack size
top = stack[-1]  # "item3"

# Works even after push/pop operations
stack.append("item4")
top = stack[-1]  # "item4"

stack.pop()
top = stack[-1]  # "item3"

print(f"Current top: {top}")
```

## 7. Error Handling
### Empty Stack Handling
```python
def safe_pop(stack):
    """Safely pop from stack with error handling"""
    try:
        return stack.pop()
    except IndexError:
        print("Error: Cannot pop from empty stack")
        return None

def safe_peek(stack):
    """Safely peek at top of stack"""
    try:
        return stack[-1]
    except IndexError:
        print("Error: Cannot peek empty stack")
        return None

# Usage
empty_stack = []
result = safe_pop(empty_stack)      # Error message, returns None
top = safe_peek(empty_stack)        # Error message, returns None

# Working stack
working_stack = ["A", "B"]
result = safe_pop(working_stack)    # Returns "B"
top = safe_peek(working_stack)     # Returns "A"
```

### Defensive Programming
```python
class SafeStack:
    """Stack with comprehensive error handling"""
    
    def __init__(self, name="Stack"):
        self.items = []
        self.name = name
    
    def push(self, item):
        """Safely push item"""
        self.items.append(item)
        print(f"{self.name}: Pushed {item}")
    
    def pop(self):
        """Safely pop item"""
        if self.is_empty():
            print(f"{self.name}: Warning - Empty stack")
            return None
        
        item = self.items.pop()
        print(f"{self.name}: Popped {item}")
        return item
    
    def peek(self):
        """Safely peek at top"""
        if self.is_empty():
            print(f"{self.name}: Warning - Empty stack")
            return None
        
        return self.items[-1]
    
    def is_empty(self):
        """Check if stack is empty"""
        return len(self.items) == 0
    
    def size(self):
        """Get stack size"""
        return len(self.items)

# Usage
safe = SafeStack("Test Stack")
safe.push("A")
safe.push("B")
safe.pop()
safe.pop()
safe.pop()  # Warning message
```

## 8. Practical Examples
### Example 1: Browser Navigation
```python
class BrowserHistory:
    """Browser history using stack"""
    
    def __init__(self):
        self.history = []
    
    def visit_page(self, page):
        """Visit a new page"""
        self.history.append(page)
        print(f"Visited: {page}")
    
    def go_back(self):
        """Go back to previous page"""
        if not self.history:
            print("No pages to go back to")
            return None
        
        current_page = self.history.pop()
        print(f"Going back from: {current_page}")
        
        if self.history:
            return self.history[-1]
        else:
            print("No more pages in history")
            return None

# Usage
browser = BrowserHistory()
browser.visit_page("homepage")
browser.visit_page("products")
browser.visit_page("checkout")

current = browser.go_back()  # Goes back to "products"
current = browser.go_back()  # Goes back to "homepage"
current = browser.go_back()  # No pages to go back to
```

### Example 2: Text Editor Undo
```python
class TextEditor:
    """Simple text editor with undo"""
    
    def __init__(self):
        self.content = ""
        self.history = []
    
    def type_text(self, text):
        """Type text and save to history"""
        self.history.append(self.content)
        self.content += text
        print(f"Typed: '{text}'")
    
    def undo(self):
        """Undo last typing"""
        if not self.history:
            print("Nothing to undo")
            return
        
        self.content = self.history.pop()
        print(f"Undo successful. Content: '{self.content}'")
    
    def get_content(self):
        """Get current content"""
        return self.content

# Usage
editor = TextEditor()
editor.type_text("Hello ")
editor.type_text("World!")
print(f"Content: '{editor.get_content()}'")

editor.undo()
print(f"After undo: '{editor.get_content()}'")

editor.undo()
print(f"After undo: '{editor.get_content()}'")
```

### Example 3: Function Call Simulation
```python
class CallStack:
    """Simulate function call stack"""
    
    def __init__(self):
        self.stack = []
    
    def call_function(self, func_name):
        """Call a function (push to stack)"""
        self.stack.append(func_name)
        print(f"Calling: {func_name}")
        self.display_stack()
    
    def return_from_function(self):
        """Return from function (pop from stack)"""
        if not self.stack:
            print("No function to return from")
            return None
        
        func_name = self.stack.pop()
        print(f"Returning from: {func_name}")
        self.display_stack()
        return func_name
    
    def display_stack(self):
        """Display current call stack"""
        print(f"Call stack: {self.stack}")
        if self.stack:
            print(f"Current function: {self.stack[-1]}")
        print()

# Usage
call_stack = CallStack()
call_stack.call_function("main")
call_stack.call_function("calculate")
call_stack.call_function("add")

call_stack.return_from_function()
call_stack.return_from_function()
call_stack.return_from_function()
```

## 9. Performance Analysis
### Time Complexity
| Operation | Description | Time Complexity | Reason |
|-----------|-------------|-----------------|---------|
| Push (append) | Add item to end | O(1) | Direct access to end |
| Pop (pop()) | Remove from end | O(1) | Direct access to end |
| Peek (stack[-1]) | Look at top | O(1) | Direct index access |
| Size (len()) | Get stack size | O(1) | Python list stores length |

### Space Complexity
- **Space**: O(n) where n is number of items in stack
- **Auxiliary Space**: O(1) for push/pop operations

### Memory Efficiency
```python
# Stack memory usage analysis
import sys

stack = []
print(f"Empty stack size: {sys.getsizeof(stack)} bytes")

stack.append("A")
print(f"After 1 item: {sys.getsizeof(stack)} bytes")

stack.append("B")
stack.append("C")
print(f"After 3 items: {sys.getsizeof(stack)} bytes")

# Note: Python lists allocate extra space for growth
```

## 10. Common Patterns and Techniques
### Pattern 1: Stack Reversal
```python
def reverse_with_stack(items):
    """Reverse a list using a stack"""
    stack = []
    
    # Push all items onto stack
    for item in items:
        stack.append(item)
    
    # Pop items to reverse order
    reversed_items = []
    while stack:
        reversed_items.append(stack.pop())
    
    return reversed_items

# Usage
original = ["A", "B", "C", "D"]
reversed_list = reverse_with_stack(original)
print(f"Original: {original}")
print(f"Reversed: {reversed_list}")
```

### Pattern 2: Stack Validation
```python
def validate_stack_operations(operations):
    """Validate if stack operations are consistent"""
    stack = []
    
    for op in operations:
        if op.startswith("push"):
            item = op.split()[1]
            stack.append(item)
        elif op == "pop":
            if not stack:
                return False  # Invalid: pop from empty stack
            stack.pop()
    
    return True  # All operations valid

# Usage
valid_ops = ["push A", "push B", "pop", "push C", "pop"]
invalid_ops = ["pop", "push A", "pop", "pop"]

print(f"Valid operations: {validate_stack_operations(valid_ops)}")
print(f"Invalid operations: {validate_stack_operations(invalid_ops)}")
```

### Pattern 3: Stack Size Tracking
```python
class TrackedStack:
    """Stack that tracks size history"""
    
    def __init__(self):
        self.items = []
        self.size_history = [0]  # Start with size 0
    
    def push(self, item):
        """Push and track size"""
        self.items.append(item)
        self.size_history.append(len(self.items))
    
    def pop(self):
        """Pop and track size"""
        if not self.items:
            return None
        
        item = self.items.pop()
        self.size_history.append(len(self.items))
        return item
    
    def get_size_history(self):
        """Get history of stack sizes"""
        return self.size_history

# Usage
tracked = TrackedStack()
tracked.push("A")
tracked.push("B")
tracked.pop()
tracked.push("C")
tracked.pop()
tracked.pop()

print(f"Size history: {tracked.get_size_history()}")
# Output: [0, 1, 2, 1, 2, 1, 0]
```

## 11. Quick Checks
- What does push do? → Adds item to top of stack
- What does pop do? → Removes and returns top item
- How do you access stack top? → stack[-1]
- Which end of list do push/pop work on? → The end (last element)
- What happens if you pop empty stack? → IndexError
- Is push/pop O(1) or O(n)? → O(1) (constant time)

## 12. Summary
Push and pop operations are the foundation of stack behavior:

### Core Operations
- **Push**: Add item to top using `append()`
- **Pop**: Remove and return top item using `pop()`
- **Top Access**: Access top item using `stack[-1]`

### Key Principles
- **LIFO Behavior**: Last item pushed is first item popped
- **Single Access Point**: Both operations work at the same end (top)
- **Constant Time**: Both operations are O(1) efficiency
- **In-Place Operations**: Modify the original list

### Implementation Details
- **Python Lists**: Natural fit with `append()` and `pop()`
- **Error Handling**: Important for empty stack operations
- **Index Access**: Top always at `stack[-1]` regardless of size
- **Memory Efficiency**: No additional space needed for operations

### Real-World Applications
- **Browser History**: Push visits, pop to go back
- **Text Editing**: Push changes, pop to undo
- **Function Calls**: Push calls, pop on return
- **Data Processing**: Push items, pop to process in reverse

> **Key Insight**: "Push and pop are like adding and removing the top book from a stack - you always work with the top item, maintaining perfect LIFO order. This simple pattern powers everything from your browser's back button to complex algorithms."

### Mastery Checklist
- ✅ Understand push operation with `append()`
- ✅ Understand pop operation with `pop()`
- ✅ Access stack top using `stack[-1]`
- ✅ Handle empty stack errors
- ✅ Implement combined push-pop sequences
- ✅ Apply to real-world scenarios
- ✅ Understand performance characteristics
- ✅ Recognize when to use stacks
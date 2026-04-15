# Building a Stack Using Lists

## 1. Introduction
Python lists provide a natural and efficient way to implement stack data structures. By using the built-in `append()` and `pop()` methods, we can create a fully functional stack that follows the LIFO (Last In, First Out) principle without any additional code. This lesson explores how to build and use stacks using Python's native list functionality.

## 2. The Photo Filter Analogy
### Visualizing Stack Behavior
Imagine editing a photo on your phone and applying filters:

```
Filter Application Order:
brightness → contrast → vignette

Stack State (Bottom to Top):
┌─────────────┐  ← Top (most recent)
│   vignette  │
├─────────────┤
│   contrast  │
├─────────────┤
│   brightness│  ← Bottom (first applied)
└─────────────┘

Undo Order (LIFO):
vignette → contrast → brightness
```

**The Process**:
1. Apply "brightness" filter → push to stack
2. Apply "contrast" filter → push to stack  
3. Apply "vignette" filter → push to stack
4. Hit "undo" → pop "vignette" (last applied)
5. Hit "undo" again → pop "contrast"
6. Hit "undo" again → pop "brightness"

## 3. Basic Stack Implementation
### Creating an Empty Stack
```python
# Initialize an empty stack
stack = []
print(f"Empty stack: {stack}")
print(f"Stack size: {len(stack)}")
print(f"Is empty: {len(stack) == 0}")
```

### Push Operations with append()
```python
# Push items onto the stack
filters = []

# Push first filter
filters.append("brightness")
print(f"After 'brightness': {filters}")

# Push second filter
filters.append("contrast")
print(f"After 'contrast': {filters}")

# Push third filter
filters.append("vignette")
print(f"After 'vignette': {filters}")

# Current stack state
print(f"Final stack: {filters}")
print(f"Top filter: {filters[-1]}")  # "vignette"
```

### Pop Operations with pop()
```python
# Pop items from the stack
filters = ["brightness", "contrast", "vignette"]
print(f"Initial: {filters}")

# Pop top filter
removed = filters.pop()
print(f"Removed: {removed}")
print(f"Remaining: {filters}")

# Pop another filter
removed = filters.pop()
print(f"Removed: {removed}")
print(f"Remaining: {filters}")

# Pop final filter
removed = filters.pop()
print(f"Removed: {removed}")
print(f"Remaining: {filters}")
```

## 4. Complete Stack Workflow
### Step-by-Step Example
```python
# Complete push/pop workflow
stack = []

print("=== Building Stack ===")
# Push phase
stack.append("X")
print(f"After push X: {stack}")

stack.append("Y")
print(f"After push Y: {stack}")

stack.append("Z")
print(f"After push Z: {stack}")

print("\n=== Using Stack ===")
# Pop phase
first = stack.pop()
print(f"Popped: {first}")
print(f"Stack now: {stack}")

second = stack.pop()
print(f"Popped: {second}")
print(f"Stack now: {stack}")

print("\n=== Checking State ===")
# Empty check
if len(stack) == 0:
    print("Stack is empty")
else:
    print("Stack is NOT empty")
    print(f"Remaining items: {stack}")
```

### Interactive Stack Demo
```python
class ListStack:
    """Stack implementation using Python list"""
    
    def __init__(self, name="Stack"):
        self.items = []
        self.name = name
    
    def push(self, item):
        """Push item onto stack"""
        self.items.append(item)
        self.display(f"Pushed {item}")
    
    def pop(self):
        """Pop item from stack"""
        if self.is_empty():
            print(f"{self.name}: Cannot pop from empty stack")
            return None
        
        item = self.items.pop()
        self.display(f"Popped {item}")
        return item
    
    def peek(self):
        """Look at top item without removing"""
        if self.is_empty():
            print(f"{self.name}: Stack is empty")
            return None
        
        return self.items[-1]
    
    def is_empty(self):
        """Check if stack is empty"""
        return len(self.items) == 0
    
    def size(self):
        """Get stack size"""
        return len(self.items)
    
    def display(self, action):
        """Display current stack state"""
        print(f"{self.name}: {action}")
        print(f"Stack: {self.items}")
        if self.items:
            print(f"Top: {self.items[-1]}")
        else:
            print("Top: None")
        print("-" * 40)

# Usage demonstration
demo_stack = ListStack("Filter Stack")
demo_stack.push("brightness")
demo_stack.push("contrast")
demo_stack.push("vignette")
demo_stack.pop()
demo_stack.pop()
demo_stack.pop()
```

## 5. Empty Stack Detection
### Methods for Checking Emptiness
```python
# Method 1: Using len() == 0
stack = []
if len(stack) == 0:
    print("Stack is empty (len method)")
else:
    print("Stack has items")

# Method 2: Using truthiness
if not stack:
    print("Stack is empty (truthiness method)")
else:
    print("Stack has items")

# Method 3: Using explicit check
if len(stack) == 0:
    print("Stack is empty (explicit check)")
else:
    print(f"Stack has {len(stack)} items")
```

### Empty Stack Handling
```python
def safe_pop(stack):
    """Safely pop from stack with empty check"""
    if len(stack) == 0:
        print("Cannot pop: stack is empty")
        return None
    
    return stack.pop()

def safe_peek(stack):
    """Safely peek at stack with empty check"""
    if len(stack) == 0:
        print("Cannot peek: stack is empty")
        return None
    
    return stack[-1]

# Usage examples
empty_stack = []
result = safe_pop(empty_stack)      # Cannot pop: stack is empty
top = safe_peek(empty_stack)        # Cannot peek: stack is empty

working_stack = ["A", "B", "C"]
result = safe_pop(working_stack)    # Returns "C"
top = safe_peek(working_stack)     # Returns "B"
```

## 6. Stack State Tracking
### Visual Stack Operations
```python
def visualize_stack_operations():
    """Visualize stack operations step by step"""
    stack = []
    
    print("Step 1: Initialize empty stack")
    print(f"Stack: {stack}")
    print(f"Empty: {len(stack) == 0}")
    print()
    
    print("Step 2: Push 'A'")
    stack.append("A")
    print(f"Stack: {stack}")
    print(f"Top: {stack[-1]}")
    print(f"Empty: {len(stack) == 0}")
    print()
    
    print("Step 3: Push 'B'")
    stack.append("B")
    print(f"Stack: {stack}")
    print(f"Top: {stack[-1]}")
    print(f"Empty: {len(stack) == 0}")
    print()
    
    print("Step 4: Push 'C'")
    stack.append("C")
    print(f"Stack: {stack}")
    print(f"Top: {stack[-1]}")
    print(f"Empty: {len(stack) == 0}")
    print()
    
    print("Step 5: Pop top item")
    popped = stack.pop()
    print(f"Popped: {popped}")
    print(f"Stack: {stack}")
    print(f"Top: {stack[-1] if stack else 'None'}")
    print(f"Empty: {len(stack) == 0}")
    print()
    
    print("Step 6: Pop another item")
    popped = stack.pop()
    print(f"Popped: {popped}")
    print(f"Stack: {stack}")
    print(f"Top: {stack[-1] if stack else 'None'}")
    print(f"Empty: {len(stack) == 0}")
    print()
    
    print("Step 7: Pop final item")
    popped = stack.pop()
    print(f"Popped: {popped}")
    print(f"Stack: {stack}")
    print(f"Top: {stack[-1] if stack else 'None'}")
    print(f"Empty: {len(stack) == 0}")

# Run visualization
visualize_stack_operations()
```

### Stack Size Monitoring
```python
class MonitoredStack:
    """Stack with size monitoring"""
    
    def __init__(self):
        self.items = []
        self.size_history = []
    
    def push(self, item):
        """Push and record size"""
        self.items.append(item)
        self.size_history.append(len(self.items))
        print(f"Pushed {item}, Size: {len(self.items)}")
    
    def pop(self):
        """Pop and record size"""
        if not self.items:
            print("Cannot pop: empty stack")
            return None
        
        item = self.items.pop()
        self.size_history.append(len(self.items))
        print(f"Popped {item}, Size: {len(self.items)}")
        return item
    
    def get_size_history(self):
        """Get history of stack sizes"""
        return self.size_history
    
    def display_history(self):
        """Display size changes over time"""
        print("Size History:")
        for i, size in enumerate(self.size_history, 1):
            print(f"  Operation {i}: Size {size}")

# Usage
monitored = MonitoredStack()
monitored.push("A")
monitored.push("B")
monitored.push("C")
monitored.pop()
monitored.pop()
monitored.pop()
monitored.display_history()
```

## 7. Practical Applications
### Application 1: Browser History Manager
```python
class BrowserHistory:
    """Browser history using list-based stack"""
    
    def __init__(self):
        self.history = []
        self.current_page = None
    
    def visit_page(self, url):
        """Visit a new page"""
        if self.current_page:
            self.history.append(self.current_page)
        self.current_page = url
        print(f"Visited: {url}")
        print(f"History: {self.history}")
    
    def go_back(self):
        """Go back to previous page"""
        if len(self.history) == 0:
            print("No pages to go back to")
            return self.current_page
        
        # Save current page
        previous_page = self.history.pop()
        self.current_page = previous_page
        print(f"Went back to: {self.current_page}")
        print(f"History: {self.history}")
        return self.current_page
    
    def get_history_count(self):
        """Get number of pages in history"""
        return len(self.history)
    
    def clear_history(self):
        """Clear all history"""
        self.history.clear()
        print("History cleared")

# Usage
browser = BrowserHistory()
browser.visit_page("https://example.com")
browser.visit_page("https://example.com/products")
browser.visit_page("https://example.com/products/item1")

browser.go_back()  # Goes back to products
browser.go_back()  # Goes back to homepage
browser.go_back()  # No pages to go back to
```

### Application 2: Text Editor with Undo
```python
class TextEditor:
    """Text editor with undo functionality"""
    
    def __init__(self):
        self.content = ""
        self.history = []
    
    def type_text(self, text):
        """Type text and save state"""
        self.history.append(self.content)
        self.content += text
        print(f"Typed: '{text}'")
        print(f"Content: '{self.content}'")
        print(f"History depth: {len(self.history)}")
    
    def undo(self):
        """Undo last typing action"""
        if len(self.history) == 0:
            print("Nothing to undo")
            return
        
        self.content = self.history.pop()
        print(f"Undo successful")
        print(f"Content: '{self.content}'")
        print(f"History depth: {len(self.history)}")
    
    def get_content(self):
        """Get current content"""
        return self.content
    
    def get_undo_count(self):
        """Get number of possible undos"""
        return len(self.history)

# Usage
editor = TextEditor()
editor.type_text("Hello ")
editor.type_text("World!")
editor.type_text(" How are you?")

editor.undo()  # Removes last addition
editor.undo()  # Removes previous addition
editor.undo()  # Removes first addition
editor.undo()  # Nothing to undo
```

### Application 3: Function Call Tracker
```python
class FunctionCallTracker:
    """Track function calls using stack"""
    
    def __init__(self):
        self.call_stack = []
        self.call_history = []
    
    def call_function(self, func_name, args=None):
        """Record function call"""
        call_info = {
            'function': func_name,
            'args': args,
            'timestamp': len(self.call_history)
        }
        self.call_stack.append(call_info)
        self.call_history.append(('call', func_name))
        print(f"Calling: {func_name}({args})")
        print(f"Call stack depth: {len(self.call_stack)}")
    
    def return_from_function(self, result=None):
        """Record function return"""
        if len(self.call_stack) == 0:
            print("No function to return from")
            return None
        
        call_info = self.call_stack.pop()
        func_name = call_info['function']
        self.call_history.append(('return', func_name, result))
        print(f"Returning from: {func_name} with result: {result}")
        print(f"Call stack depth: {len(self.call_stack)}")
        return result
    
    def get_current_function(self):
        """Get currently executing function"""
        if len(self.call_stack) == 0:
            return None
        
        return self.call_stack[-1]['function']
    
    def get_call_stack_depth(self):
        """Get current call stack depth"""
        return len(self.call_stack)

# Usage
tracker = FunctionCallTracker()
tracker.call_function("main")
tracker.call_function("calculate", [1, 2, 3])
tracker.call_function("add", [1, 2])

tracker.return_from_function(3)
tracker.return_from_function(6)
tracker.return_from_function("done")
```

## 8. Performance Considerations
### Time Complexity Analysis
```python
import time

def measure_stack_performance():
    """Measure performance of stack operations"""
    stack = []
    iterations = 100000
    
    # Measure push performance
    start_time = time.time()
    for i in range(iterations):
        stack.append(f"item_{i}")
    push_time = time.time() - start_time
    
    # Measure pop performance
    start_time = time.time()
    while stack:
        stack.pop()
    pop_time = time.time() - start_time
    
    print(f"Push operations: {iterations:,} in {push_time:.4f} seconds")
    print(f"Pop operations: {iterations:,} in {pop_time:.4f} seconds")
    print(f"Average push time: {(push_time/iterations)*1000000:.2f} microseconds")
    print(f"Average pop time: {(pop_time/iterations)*1000000:.2f} microseconds")

# Run performance test
measure_stack_performance()
```

### Memory Usage Analysis
```python
import sys

def analyze_memory_usage():
    """Analyze memory usage of list-based stacks"""
    sizes = [0, 10, 100, 1000, 10000]
    
    for size in sizes:
        stack = []
        
        # Add items to stack
        for i in range(size):
            stack.append(f"item_{i}")
        
        # Measure memory usage
        memory_bytes = sys.getsizeof(stack)
        memory_kb = memory_bytes / 1024
        
        print(f"Stack size {size:,}: {memory_bytes:,} bytes ({memory_kb:.2f} KB)")

# Run memory analysis
analyze_memory_usage()
```

## 9. Common Patterns and Techniques
### Pattern 1: Stack Reversal
```python
def reverse_with_stack(items):
    """Reverse a list using stack operations"""
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
original = ["first", "second", "third", "fourth"]
reversed_list = reverse_with_stack(original)
print(f"Original: {original}")
print(f"Reversed: {reversed_list}")
```

### Pattern 2: Stack Validation
```python
def validate_stack_sequence(operations):
    """Validate if a sequence of operations is valid"""
    stack = []
    
    for op in operations:
        if op == "push":
            # Simulate push without knowing the item
            stack.append("item")
        elif op == "pop":
            if len(stack) == 0:
                return False  # Invalid: pop from empty stack
            stack.pop()
        else:
            return False  # Invalid operation
    
    return True  # All operations valid

# Usage
valid_sequence = ["push", "push", "pop", "push", "pop", "pop"]
invalid_sequence = ["pop", "push", "pop", "pop"]

print(f"Valid sequence: {validate_stack_sequence(valid_sequence)}")
print(f"Invalid sequence: {validate_stack_sequence(invalid_sequence)}")
```

### Pattern 3: Stack Comparison
```python
def compare_stacks(stack1, stack2):
    """Compare two stacks without modifying them"""
    # Create temporary copies
    temp1 = stack1.copy()
    temp2 = stack2.copy()
    
    # Compare sizes first
    if len(temp1) != len(temp2):
        return False
    
    # Compare items from top to bottom
    while temp1 and temp2:
        item1 = temp1.pop()
        item2 = temp2.pop()
        if item1 != item2:
            return False
    
    return True

# Usage
stack_a = ["A", "B", "C"]
stack_b = ["A", "B", "C"]
stack_c = ["A", "B", "D"]

print(f"Stack A == Stack B: {compare_stacks(stack_a, stack_b)}")
print(f"Stack A == Stack C: {compare_stacks(stack_a, stack_c)}")
```

## 10. Error Handling and Edge Cases
### Comprehensive Error Handling
```python
class RobustStack:
    """Stack with comprehensive error handling"""
    
    def __init__(self, max_size=None):
        self.items = []
        self.max_size = max_size
    
    def push(self, item):
        """Push with error handling"""
        if self.max_size and len(self.items) >= self.max_size:
            print(f"Error: Stack overflow (max size: {self.max_size})")
            return False
        
        self.items.append(item)
        return True
    
    def pop(self):
        """Pop with error handling"""
        if len(self.items) == 0:
            print("Error: Stack underflow")
            return None
        
        return self.items.pop()
    
    def peek(self):
        """Peek with error handling"""
        if len(self.items) == 0:
            print("Error: Cannot peek empty stack")
            return None
        
        return self.items[-1]
    
    def is_full(self):
        """Check if stack is full"""
        return self.max_size and len(self.items) >= self.max_size
    
    def is_empty(self):
        """Check if stack is empty"""
        return len(self.items) == 0

# Usage
robust = RobustStack(max_size=3)
robust.push("A")
robust.push("B")
robust.push("C")
robust.push("D")  # Error: Stack overflow

robust.pop()
robust.pop()
robust.pop()
robust.pop()  # Error: Stack underflow
```

## 11. Quick Checks
- How do you create an empty stack? → `stack = []`
- How do you push an item? → `stack.append(item)`
- How do you pop an item? → `stack.pop()`
- How do you check if empty? → `len(stack) == 0`
- How do you access top? → `stack[-1]`
- What happens if you pop empty stack? → IndexError

## 12. Summary
Building a stack using Python lists is straightforward and efficient:

### Core Implementation
- **Empty Stack**: `stack = []`
- **Push Operation**: `stack.append(item)`
- **Pop Operation**: `stack.pop()`
- **Empty Check**: `len(stack) == 0`
- **Top Access**: `stack[-1]`

### Key Advantages
- **Natural Fit**: Python lists are designed for these operations
- **Constant Time**: All operations are O(1)
- **Built-in Methods**: No custom implementation needed
- **Memory Efficient**: No overhead beyond the list itself

### Common Patterns
- **Workflow Management**: Browser history, undo systems
- **Data Processing**: Reversing sequences, validation
- **Function Tracking**: Call stacks, execution context
- **State Management**: Saving and restoring states

### Error Handling
- **Empty Stack**: Always check before popping
- **Index Errors**: Use safe methods or try-catch
- **Memory Limits**: Consider maximum stack size
- **Type Safety**: Ensure consistent data types

### Performance Characteristics
- **Time Complexity**: O(1) for all basic operations
- **Space Complexity**: O(n) for n items
- **Memory Overhead**: Minimal (just the list)
- **Scalability**: Excellent for most use cases

> **Key Insight**: "Python lists are perfect for stacks because they're designed for efficient end operations. Using `append()` and `pop()` gives you a fully functional stack with no extra code - it's like the language was built with stacks in mind."

### Mastery Checklist
- ✅ Create empty stack with list
- ✅ Implement push with `append()`
- ✅ Implement pop with `pop()`
- ✅ Check for empty stack
- ✅ Access top element safely
- ✅ Handle errors appropriately
- ✅ Apply to real-world scenarios
- ✅ Understand performance implications
# Edge Cases and Reliability in Array Operations

## 1. Introduction
Edge cases are situations that occur at the extreme ends of input ranges or with unusual data configurations. In array operations, common edge cases include empty lists, single-element lists, and accessing indices that don't exist. This lesson teaches you to write reliable code that handles these situations gracefully.

## 2. The IndexError Problem
### What Happens with Short Lists?
When you assume indices always exist, your code can crash:

```python
# Works fine with 3 elements
scores = [950, 880, 790]
print("Top score:", scores[0])    # 950
print("Second score:", scores[1]) # 880
print("Third score:", scores[2])  # 790

# Crashes with only 1 element
scores = [950]
print("Top score:", scores[0])    # 950 - works
print("Second score:", scores[1]) # IndexError: list index out of range
print("Third score:", scores[2])  # Never reached
```

### Identifying Unsafe Access
For `scores = [950]`:
- `scores[0]` is **safe** (the only element)
- `scores[1]` is **unsafe** (first index that doesn't exist)
- `scores[2]` is **unsafe** (also doesn't exist)

## 3. The Length Gate Pattern
### Basic Guard Clause
Use length checks before accessing potentially unsafe indices:

```python
scores = [950]

if len(scores) >= 3:
    print(scores[0], scores[1], scores[2])
else:
    print("Not enough scores yet.")
```

### Why This Works
- **Prevention**: Never attempts unsafe access
- **Graceful degradation**: Provides fallback behavior
- **No crashes**: Works for any list length (0, 1, 2, 3+)

## 4. Common Edge Case Patterns
### Pattern 1: Safe First-Last-Middle Access
```python
def get_boundary_elements(lst):
    """Safely get first, middle, and last elements"""
    result = {}
    
    if len(lst) >= 1:
        result['first'] = lst[0]
    
    if len(lst) >= 3:
        result['middle'] = lst[len(lst) // 2]
    
    if len(lst) >= 2:
        result['last'] = lst[-1]
    
    return result

# Usage examples
print(get_boundary_elements([10, 8, 5, 3]))  # {'first': 10, 'middle': 5, 'last': 3}
print(get_boundary_elements([9, 7]))         # {'first': 9, 'last': 7}
print(get_boundary_elements([4]))           # {'first': 4}
print(get_boundary_elements([]))            # {}
```

### Pattern 2: Safe Top-N Extraction
```python
def get_top_n(lst, n=3):
    """Safely get top N elements with fallback"""
    if len(lst) >= n:
        return lst[:n]  # Return first n elements
    else:
        return []       # Safe fallback for short lists

# Usage
print(get_top_n([10, 8, 5, 3, 2]))  # [10, 8, 5]
print(get_top_n([4, 2, 1]))         # [4, 2, 1]
print(get_top_n([9, 7]))            # []
print(get_top_n([]))                # []
```

### Pattern 3: Conditional Processing
```python
def process_if_possible(lst, min_length=2):
    """Process list only if it meets minimum requirements"""
    if len(lst) < min_length:
        return f"Need at least {min_length} items, got {len(lst)}"
    
    # Safe to process - we know we have enough elements
    first = lst[0]
    last = lst[-1]
    total = sum(lst)
    
    return f"Processed {len(lst)} items: {first}...{last}, total={total}"

# Usage
print(process_if_possible([1, 2, 3, 4]))  # "Processed 4 items: 1...4, total=10"
print(process_if_possible([5]))         # "Need at least 2 items, got 1"
print(process_if_possible([]))           # "Need at least 2 items, got 0"
```

## 5. Writing Safe Helper Functions
### The get_top_three Function
```python
def get_top_three(lst):
    """Return first three elements if available, otherwise empty list"""
    if len(lst) >= 3:
        result = [lst[0], lst[1], lst[2]]
        return result
    else:
        return []

# Test cases
print(get_top_three([10, 8, 5, 3]))  # [10, 8, 5]
print(get_top_three([4, 2, 1]))      # [4, 2, 1]
print(get_top_three([9, 7]))         # []
print(get_top_three([]))             # []
```

### Alternative Implementation
```python
def get_top_three_slice(lst):
    """More concise version using slicing"""
    return lst[:3] if len(lst) >= 3 else []

# Same behavior, more compact
print(get_top_three_slice([10, 8, 5, 3]))  # [10, 8, 5]
print(get_top_three_slice([9, 7]))         # []
```

## 6. Common Edge Case Scenarios
### Scenario 1: Empty List Processing
```python
def find_max_safe(numbers):
    """Find maximum value safely"""
    if not numbers:  # Empty list check
        return None
    
    max_val = numbers[0]
    for num in numbers[1:]:
        if num > max_val:
            max_val = num
    return max_val

# Usage
print(find_max_safe([3, 7, 2, 9]))  # 9
print(find_max_safe([5]))           # 5
print(find_max_safe([]))            # None
```

### Scenario 2: Single Element Lists
```python
def get_range_safe(numbers):
    """Get range (max - min) safely"""
    if len(numbers) < 2:
        return 0  # No range for 0 or 1 elements
    
    return max(numbers) - min(numbers)

# Usage
print(get_range_safe([1, 5, 3, 9]))  # 8 (9 - 1)
print(get_range_safe([7]))           # 0 (single element)
print(get_range_safe([]))            # 0 (empty)
```

### Scenario 3: Middle Element Access
```python
def get_middle_safe(lst):
    """Get middle element safely"""
    if len(lst) == 0:
        return None
    elif len(lst) == 1:
        return lst[0]
    else:
        return lst[len(lst) // 2]

# Usage
print(get_middle_safe([1, 2, 3, 4, 5]))  # 3
print(get_middle_safe([10, 20, 30]))     # 20
print(get_middle_safe([7]))               # 7
print(get_middle_safe([]))                # None
```

## 7. Defensive Programming Techniques
### Technique 1: Validate Input Length
```python
def safe_list_operation(lst, required_length):
    """Generic safe operation pattern"""
    if len(lst) < required_length:
        raise ValueError(f"Need at least {required_length} elements, got {len(lst)}")
    
    # Safe to proceed with operation
    return lst[:required_length]

# Usage
try:
    result = safe_list_operation([1, 2, 3], 3)
    print(result)  # [1, 2, 3]
    
    result = safe_list_operation([1, 2], 3)  # Raises ValueError
except ValueError as e:
    print(f"Error: {e}")
```

### Technique 2: Return Default Values
```python
def safe_access(lst, index, default=None):
    """Access list element with default fallback"""
    if 0 <= index < len(lst):
        return lst[index]
    else:
        return default

# Usage
print(safe_access([1, 2, 3], 1))        # 2
print(safe_access([1, 2, 3], 5))        # None
print(safe_access([1, 2, 3], -1, "N/A")) # "N/A"
```

### Technique 3: Try-Except for Exception Handling
```python
def safe_get_element(lst, index, default=None):
    """Try-except approach for safe access"""
    try:
        return lst[index]
    except IndexError:
        return default

# Usage
print(safe_get_element([1, 2, 3], 1))  # 2
print(safe_get_element([1, 2, 3], 5))  # None
```

## 8. Testing Edge Cases
### Comprehensive Test Suite
```python
def test_get_top_three():
    """Test get_top_three with various edge cases"""
    test_cases = [
        # (input, expected_output, description)
        ([10, 8, 5, 3], [10, 8, 5], "4 elements"),
        ([4, 2, 1], [4, 2, 1], "exactly 3 elements"),
        ([9, 7], [], "2 elements"),
        ([5], [], "1 element"),
        ([], [], "empty list"),
    ]
    
    for i, (input_list, expected, description) in enumerate(test_cases):
        result = get_top_three(input_list)
        assert result == expected, f"Test {i+1} failed: {description}"
        print(f"✓ Test {i+1} passed: {description}")

# Run tests
test_get_top_three()
```

### Boundary Testing
```python
def test_boundary_conditions():
    """Test functions at boundary conditions"""
    functions_to_test = [
        (get_top_three, [0, 1, 2, 3]),  # Test at exactly 3 elements
        (get_top_three, [0, 1]),        # Test below threshold
        (get_top_three, []),             # Test empty
    ]
    
    for func, test_input in functions_to_test:
        try:
            result = func(test_input)
            print(f"{func.__name__}({test_input}) = {result}")
        except Exception as e:
            print(f"{func.__name__}({test_input}) crashed: {e}")

test_boundary_conditions()
```

## 9. Common Mistakes and Solutions
### Mistake 1: Assuming Indices Always Exist
```python
# WRONG - Assumes list has at least 3 elements
def get_stats_wrong(lst):
    first = lst[0]
    middle = lst[len(lst) // 2]
    last = lst[-1]
    return first, middle, last

# CORRECT - Checks length first
def get_stats_right(lst):
    if len(lst) == 0:
        return None, None, None
    elif len(lst) == 1:
        return lst[0], lst[0], lst[0]
    elif len(lst) == 2:
        return lst[0], lst[0], lst[1]
    else:
        return lst[0], lst[len(lst) // 2], lst[-1]
```

### Mistake 2: Incorrect Length Conditions
```python
# WRONG - Uses wrong comparison
if len(items) <= 3:
    middle = items[1]  # Crashes for empty or single-element lists

# CORRECT - Uses appropriate condition
if len(items) >= 3:
    middle = items[len(items) // 2]
```

### Mistake 3: Unsafe Middle Element Access
```python
# WRONG - Crashes on empty lists
def get_middle_wrong(lst):
    return lst[len(lst) // 2]

# CORRECT - Handles empty lists safely
def get_middle_right(lst):
    if len(lst) == 0:
        return None
    return lst[len(lst) // 2]

# Example of the crash
items = []
# get_middle_wrong(items)  # IndexError: list index out of range
# get_middle_right(items)  # Returns None safely
```

## 10. Quick Checks
- What happens when you access `lst[1]` on a single-element list? → IndexError
- How do you safely access the middle element? → Check `len(lst) >= 3` first
- What's a "length gate"? → `if len(lst) >= required:` before accessing indices
- Why is `items[len(items) // 2]` unsafe for empty lists? → Computes index 0, but list is empty

## 11. Summary
Edge case handling is essential for reliable array operations:

### Core Principles
- **Prevention over reaction**: Check conditions before accessing
- **Graceful degradation**: Provide fallback behavior
- **Defensive programming**: Assume inputs can be invalid

### Key Patterns
- **Length gates**: `if len(lst) >= required:` before accessing
- **Safe helpers**: Functions that handle edge cases internally
- **Default values**: Return sensible defaults for invalid cases
- **Exception handling**: Use try-except when appropriate

### Common Edge Cases
- **Empty lists**: No elements to access
- **Single-element lists**: Only index 0 is safe
- **Short lists**: Not enough elements for multi-element operations
- **Index calculations**: May compute valid-looking but unsafe indices

### Best Practices
- Always validate list length before accessing specific indices
- Write helper functions that encapsulate safety logic
- Test with boundary conditions (0, 1, 2, exactly threshold, above threshold)
- Use descriptive error messages or fallback values

> **Key Insight**: "Reliable code anticipates edge cases rather than reacting to crashes. A simple length check can prevent most IndexError problems."

### Mastery Checklist
- ✅ Identify unsafe index access patterns
- ✅ Implement length gates for safe access
- ✅ Write helper functions with fallback behavior
- ✅ Handle empty, single-element, and short lists
- ✅ Use defensive programming techniques
- ✅ Test boundary conditions systematically
- ✅ Choose appropriate error handling strategies
- ✅ Write code that never crashes from IndexError
# Implementing High Dimensional Arrays in Python

## 1. Introduction
This lesson focuses on the practical implementation of high dimensional arrays in Python using nested lists. You'll learn how to create, access, and modify multi-dimensional data structures while maintaining their shape and structure.

## 2. Creating Nested Lists
### Basic 2D Structure
A nested list is a list where each element is itself another list:

```python
# Cinema seating: 3 rows, 4 seats per row
seats = [
    ["A1", "A2", "A3", "A4"],  # Row 0
    ["B1", "B2", "B3", "B4"],  # Row 1
    ["C1", "C2", "C3", "C4"]   # Row 2
]
```

### Understanding the Structure
- **Outer list**: Represents the entire cinema (all rows)
- **Inner lists**: Each represents one row of seats
- **Individual elements**: Each represents a specific seat

## 3. Accessing Nested Elements
### Two-Index Pattern
Access elements using chained brackets: `array[row][column]`

```python
seats = [
    ["A1", "A2", "A3", "A4"],
    ["B1", "B2", "B3", "B4"],
    ["C1", "C2", "C3", "C4"]
]

# Access an entire row
row_1 = seats[1]  # ['B1', 'B2', 'B3', 'B4']

# Access a specific seat
seat_c3 = seats[2][2]  # 'C3' (Row 2, Column 2)
```

### Index Breakdown
- First index: selects which inner list (row)
- Second index: selects element within that inner list (seat)

## 4. Modifying Nested Elements
### In-Place Updates
Modify individual elements without changing the overall structure:

```python
seats = [
    ["A1", "A2", "A3", "A4"],
    ["B1", "B2", "B3", "B4"],
    ["C1", "C2", "C3", "C4"]
]

# Mark seat B2 as reserved
seats[1][1] = "X"

print(seats)
# [['A1', 'A2', 'A3', 'A4'],
#  ['B1', 'X', 'B3', 'B4'],
#  ['C1', 'C2', 'C3', 'C4']]
```

### Key Points
- Only the targeted element changes
- The overall structure (3 rows × 4 seats) remains intact
- Other elements in the same row/column are unaffected

## 5. Common Patterns
### Pattern 1: Grid Creation
```python
# Method 1: Direct initialization
grid = [
    [0, 0, 0],
    [0, 0, 0],
    [0, 0, 0]
]

# Method 2: Using loops
rows, cols = 3, 3
grid = []
for row in range(rows):
    new_row = []
    for col in range(cols):
        new_row.append(0)
    grid.append(new_row)

# Method 3: List comprehension
grid = [[0 for col in range(cols)] for row in range(rows)]
```

### Pattern 2: Element Access and Modification
```python
def update_seat(seating_chart, row, col, new_value):
    """Update a specific seat in the seating chart"""
    if 0 <= row < len(seating_chart) and 0 <= col < len(seating_chart[row]):
        old_value = seating_chart[row][col]
        seating_chart[row][col] = new_value
        return f"Changed {old_value} to {new_value} at ({row}, {col})"
    else:
        return f"Invalid position ({row}, {col})"

# Usage
seats = [
    ["A1", "A2", "A3", "A4"],
    ["B1", "B2", "B3", "B4"],
    ["C1", "C2", "C3", "C4"]
]

result = update_seat(seats, 1, 1, "X")
print(result)  # "Changed B2 to X at (1, 1)"
```

### Pattern 3: Iterating Through Grids
```python
# Method 1: Using enumerate for indices
for row_idx, row in enumerate(seats):
    for col_idx, seat in enumerate(row):
        print(f"Seat at ({row_idx}, {col_idx}): {seat}")

# Method 2: Using range for indices
for row_idx in range(len(seats)):
    for col_idx in range(len(seats[row_idx])):
        seat = seats[row_idx][col_idx]
        print(f"Seat at ({row_idx}, {col_idx}): {seat}")
```

## 6. Practical Examples
### Example 1: Tic-Tac-Toe Board
```python
# Create empty board
board = [
    [" ", " ", " "],
    [" ", " ", " "],
    [" ", " ", " "]
]

# Make moves
board[0][0] = "X"  # Top-left corner
board[1][1] = "O"  # Center
board[2][2] = "X"  # Bottom-right corner

print("Tic-Tac-Toe Board:")
for row in board:
    print("|".join(row))
    print("-" * 5)
```

### Example 2: Weekly Schedule
```python
# Days × Time slots
schedule = [
    ["Math", "English", "PE"],      # Monday
    ["History", "Science", "Art"],   # Tuesday
    ["Music", "Geography", "Math"],  # Wednesday
    ["English", "Math", "History"],  # Thursday
    ["Science", "Art", "PE"]         # Friday
]

# Access Wednesday's second class
wednesday_second = schedule[2][1]  # "Geography"

# Update Thursday's first class
schedule[3][0] = "Literature"

print("Updated Schedule:")
days = ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday"]
for day_idx, day in enumerate(days):
    print(f"{day}: {', '.join(schedule[day_idx])}")
```

### Example 3: Game Board with Coordinates
```python
# 5x5 adventure game board
game_board = [
    [".", ".", ".", ".", "."],
    [".", "T", ".", "M", "."],  # T = Treasure, M = Monster
    [".", ".", ".", ".", "."],
    [".", "K", ".", ".", "."],  # K = Key
    [".", ".", ".", ".", "."]
]

def find_items(board):
    """Find all special items and their coordinates"""
    items = {}
    for row_idx, row in enumerate(board):
        for col_idx, cell in enumerate(row):
            if cell != ".":
                items[cell] = (row_idx, col_idx)
    return items

items_found = find_items(game_board)
print("Items found:")
for item, location in items_found.items():
    print(f"{item} at position {location}")
```

## 7. Common Indexing Mistakes
### Mistake 1: Using Commas Instead of Brackets
```python
# WRONG
seats[1, 1] = "X"  # SyntaxError

# CORRECT
seats[1][1] = "X"
```

### Mistake 2: Forgetting 0-Based Indexing
```python
seats = [
    ["A1", "A2", "A3", "A4"],  # Row 0
    ["B1", "B2", "B3", "B4"],  # Row 1
    ["C1", "C2", "C3", "C4"]   # Row 2
]

# "C4" is at row 2, column 3 (not row 3, column 4)
correct = seats[2][3]  # "C4"
```

### Mistake 3: Index Out of Range
```python
# Check bounds before accessing
def safe_access(grid, row, col):
    if 0 <= row < len(grid) and 0 <= col < len(grid[row]):
        return grid[row][col]
    else:
        return None  # or raise an error
```

## 8. Working with Different Dimensions
### 1D vs 2D vs 3D Access Patterns
```python
# 1D array
one_d = [10, 20, 30]
value = one_d[1]  # Single index

# 2D array
two_d = [[1, 2], [3, 4]]
value = two_d[0][1]  # Row 0, Column 1

# 3D array
three_d = [[[1, 2], [3, 4]], [[5, 6], [7, 8]]]
value = three_d[0][1][0]  # Layer 0, Row 1, Column 0
```

### Creating Different Sized Grids
```python
# Rectangular grid (not square)
rectangular = [
    [1, 2, 3, 4],   # 4 columns
    [5, 6, 7, 8],   # 4 columns
    [9, 10, 11, 12] # 4 columns
]

# Jagged array (different row lengths)
jagged = [
    [1, 2, 3],      # 3 elements
    [4, 5],         # 2 elements
    [6, 7, 8, 9]    # 4 elements
]
```

## 9. Debugging Tips
### Visualizing the Structure
```python
def print_grid_structure(grid):
    """Print grid with row and column indices"""
    print("   ", end="")
    for col in range(len(grid[0]) if grid else 0):
        print(f"{col:3}", end="")
    print()
    
    for row_idx, row in enumerate(grid):
        print(f"{row_idx:2}:", end="")
        for col_idx, value in enumerate(row):
            print(f"{str(value):3}", end="")
        print()

# Usage
seats = [
    ["A1", "A2", "A3", "A4"],
    ["B1", "X", "B3", "B4"],
    ["C1", "C2", "C3", "C4"]
]
print_grid_structure(seats)
```

### Checking Array Dimensions
```python
def get_dimensions(array):
    """Get dimensions of nested array"""
    if not isinstance(array, list):
        return 0
    elif not array or not isinstance(array[0], list):
        return 1
    elif not array[0] or not isinstance(array[0][0], list):
        return 2
    else:
        return 3

# Usage
print(get_dimensions([1, 2, 3]))           # 1D
print(get_dimensions([[1, 2], [3, 4]]))    # 2D
print(get_dimensions([[[1], [2]], [[3], [4]]]))  # 3D
```

## 10. Quick Checks
- How do you access element in 2D array? → `array[row][column]`
- What's wrong with `seats[1, 1]`? → Use brackets, not commas: `seats[1][1]`
- How do you modify element at row 2, column 3? → `array[2][3] = new_value`
- What does `seats[1]` return? → The entire row at index 1

## 11. Summary
Implementing high dimensional arrays in Python uses nested lists:

### Core Skills
- **Create nested lists** using bracket syntax within brackets
- **Access elements** with chained indices: `array[row][column]`
- **Modify elements** in-place while preserving structure
- **Understand 0-based indexing** for both dimensions

### Key Patterns
- **Grid creation**: Direct definition, loops, or list comprehensions
- **Safe access**: Check bounds before accessing elements
- **Iteration**: Use nested loops with `enumerate()` or `range()`
- **Common applications**: Game boards, schedules, seating charts

### Best Practices
- Use descriptive variable names (`row_idx`, `col_idx`)
- Validate indices before access to avoid errors
- Visualize structure when debugging complex arrays
- Start with simple examples before moving to complex patterns

> **Key Insight**: "Nested lists in Python follow the same pattern as regular lists - just add more brackets for each dimension you need."

### Mastery Checklist
- ✅ Create 2D arrays using nested list syntax
- ✅ Access elements using multiple indices
- ✅ Modify elements while preserving structure
- ✅ Iterate through 2D arrays correctly
- ✅ Handle common indexing mistakes
- ✅ Apply patterns to real-world problems
- ✅ Debug and visualize array structures
- ✅ Understand when to use different dimensions
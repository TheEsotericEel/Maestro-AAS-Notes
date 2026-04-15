# Introducing High Dimensional Arrays

## 1. Introduction
High dimensional arrays are arrays where each element can itself be an array. This creates multi-level data structures like 2D grids (rows and columns) or 3D structures (layers of grids). Think of them as "arrays of arrays" that can be nested to represent complex real-world data.

## 2. From 1D to 2D: The Cinema Analogy
### Single Row (1D)
```python
# One row of cinema seats
row = ["A1", "A2", "A3", "A4", "A5"]
# This is a 1D array - just a single list
```

### Multiple Rows (2D)
```python
# Whole cinema with multiple rows
cinema = [
    ["A1", "A2", "A3", "A4", "A5"],  # Row 0
    ["B1", "B2", "B3", "B4", "B5"],  # Row 1
    ["C1", "C2", "C3", "C4", "C5"]   # Row 2
]
# This is a 2D array - an array of arrays
```

**Key Insight**: A 2D array is a list where each element is itself a list (each row is a list of seats).

## 3. Understanding 2D Array Coordinates
### Position vs Value
In a 2D array, you need two positions to find one element:

```python
grid = [
    [2, 5, 7, 9],   # Row 0
    [4, 1, 8, 3],   # Row 1
    [6, 0, 11, 10]  # Row 2
]

# To find value 8:
row_index = 1      # Second row
col_index = 2      # Third column
value = grid[row_index][col_index]  # grid[1][2] = 8
```

**Coordinate Format**: `(row, column)` - both are indexes (positions), not the actual values.

## 4. Real-World 2D Examples
### Chessboard
```python
# 8x8 chessboard
chessboard = [
    ["♜", "♞", "♝", "♛", "♚", "♝", "♞", "♜"],
    ["♟", "♟", "♟", "♟", "♟", "♟", "♟", "♟"],
    [" ", " ", " ", " ", " ", " ", " ", " "],
    [" ", " ", " ", " ", " ", " ", " ", " "],
    [" ", " ", " ", " ", " ", " ", " ", " "],
    [" ", " ", " ", " ", " ", " ", " ", " "],
    ["♙", "♙", "♙", "♙", "♙", "♙", "♙", "♙"],
    ["♖", "♘", "♗", "♕", "♔", "♗", "♘", "♖"]
]

# Access a specific square
piece = chessboard[0][0]  # Top-left corner: "♜"
```

### Weekly Timetable
```python
# School timetable: days × time slots
timetable = [
    ["Math", "English", "PE"],      # Monday
    ["History", "Science", "Art"],   # Tuesday
    ["Music", "Geography", "Math"],  # Wednesday
    ["English", "Math", "History"],  # Thursday
    ["Science", "Art", "PE"]         # Friday
]

# Wednesday's second class
wednesday_second = timetable[2][1]  # "Geography"
```

## 5. Going to 3D: Stacking Layers
### Warehouse Shelves Analogy
```python
# 3D warehouse: shelves × rows × boxes
warehouse = [
    # Shelf 0 (front)
    [
        ["box", "box", "box"],  # Row 0
        ["box", "box", "box"]   # Row 1
    ],
    # Shelf 1 (middle)
    [
        ["box", "box", "box"],  # Row 0
        ["box", "box", "box"]   # Row 1
    ],
    # Shelf 2 (back)
    [
        ["box", "box", "box"],  # Row 0
        ["box", "box", "box"]   # Row 1
    ]
]

# Find a specific box: (shelf, row, column)
specific_box = warehouse[1][0][2]  # Shelf 1, Row 0, Column 2
```

### Image Layers in Photo Editor
```python
# 3D image: layers × rows × pixels
image_layers = [
    # Layer 0 (background)
    [
        [255, 255, 255, 255],  # Row 0 pixels
        [255, 255, 255, 255],  # Row 1 pixels
        [255, 255, 255, 255]   # Row 2 pixels
    ],
    # Layer 1 (middle)
    [
        [0, 0, 0, 0],
        [0, 255, 255, 0],
        [0, 0, 0, 0]
    ],
    # Layer 2 (foreground)
    [
        [255, 0, 0, 255],
        [0, 255, 0, 0],
        [255, 0, 0, 255]
    ]
]

# Access pixel: (layer, row, column)
pixel = image_layers[1][1][2]  # Layer 1, Row 1, Column 2
```

## 6. Accessing Elements in High Dimensional Arrays
### 1D Access
```python
one_d = [10, 20, 30, 40]
value = one_d[2]  # Single index
```

### 2D Access
```python
two_d = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]
value = two_d[1][2]  # Row 1, Column 2 = 6
```

### 3D Access
```python
three_d = [
    [[1, 2], [3, 4]],
    [[5, 6], [7, 8]]
]
value = three_d[0][1][0]  # Layer 0, Row 1, Column 0 = 3
```

## 7. Common Patterns
### Iterating Through 2D Arrays
```python
grid = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

# Method 1: By rows
for row_index, row in enumerate(grid):
    for col_index, value in enumerate(row):
        print(f"({row_index}, {col_index}) = {value}")

# Method 2: By coordinates
for row_index in range(len(grid)):
    for col_index in range(len(grid[row_index])):
        value = grid[row_index][col_index]
        print(f"({row_index}, {col_index}) = {value}")
```

### Creating 2D Arrays
```python
# Method 1: Direct definition
matrix = [
    [0, 0, 0],
    [0, 0, 0],
    [0, 0, 0]
]

# Method 2: Using loops
rows, cols = 3, 4
matrix = []
for row in range(rows):
    new_row = []
    for col in range(cols):
        new_row.append(0)
    matrix.append(new_row)

# Method 3: List comprehension
matrix = [[0 for col in range(cols)] for row in range(rows)]
```

## 8. When to Use High Dimensional Arrays
### Use 2D When:
- Data naturally forms a grid (chessboard, spreadsheet)
- You need row/column relationships
- Geographic or spatial data
- Image processing (pixels × pixels)

### Use 3D When:
- Stacking multiple 2D layers
- Time series of 2D data
- 3D spatial data (x, y, z coordinates)
- Multiple images/layers

### Stick to 1D When:
- Simple list of items
- No inherent grid structure
- Linear sequence is natural

## 9. Quick Checks
- What is a 2D array? → An array of arrays (list of rows)
- How do you access element in 2D? → `array[row][column]`
- What's a real 2D example? → Chessboard, spreadsheet, cinema seating
- What's a 3D coordinate? → `(layer, row, column)` or `(depth, row, column)`

## 10. Summary
High dimensional arrays extend the 1D array concept by nesting arrays within arrays:
- **1D**: Single list of items
- **2D**: Grid structure (array of rows, each row is array of columns)
- **3D**: Stacked grids (array of layers, each layer is 2D array)

The key is recognizing when your data naturally fits a multi-level structure and using appropriate coordinate systems to access elements.

> **Key Insight**: "High dimensional arrays are just arrays of arrays - the same concept you already know, nested to match real-world grid or layered data."
# Using Arrays for Structured Problem Solving

## 1. Introduction
Structured problem solving with arrays means turning a goal into a clear sequence of list operations. Start with a small storyboard in words, then translate each step into Python list methods while tracking how indices change.

## 2. Storyboard First, Code Second
### Example Goal
Start:
```python
tasks = ["email boss", "write report", "coffee break", "team meeting"]
```
Target:
```python
["coffee break", "email boss", "team meeting"]
```

### Plain-English Storyboard
1) Remove "write report" (index 1)
2) Remove "coffee break" (now at index 1)
3) Insert "coffee break" at index 0

Turning the story into code keeps you intentional and prevents index mistakes.

## 3. Translating the Storyboard to Code
```python
tasks = ["email boss", "write report", "coffee break", "team meeting"]

tasks.pop(1)                # remove "write report"
coffee = tasks.pop(1)       # remove "coffee break" (now at index 1)
tasks.insert(0, coffee)     # insert at front

print(tasks)  # ['coffee break', 'email boss', 'team meeting']
```

## 4. Index Awareness (Shifts After Removal)
Removing an item shifts everything to the left:
```python
nums = [10, 20, 30, 40, 50]
nums.pop(1)         # removes 20
# nums -> [10, 30, 40, 50]
# index 1 is now 30, index 2 is now 40
```
Always ask: "What is at this index *now* after previous operations?"

## 5. Moving an Item to a New Position
Pattern: pop to capture → insert at new index.
```python
playlist = ["intro", "song A", "song B", "song C"]

playlist.pop(1)          # remove "song A"
song_b = playlist.pop(1)  # remove "song B" (now at index 1)
playlist.insert(0, song_b)

print(playlist)  # ['song B', 'intro', 'song C']
```

## 6. Designing Input and Output
- **Input**: a defined starting list
- **Operations**: access, update, remove, insert in a planned order
- **Output**: final list (and optional return values like removed items or new length)

## 7. Common Patterns
- **Storyboard first**: write the steps in words before coding.
- **Access → Update → Remove/Insert**: keep a deliberate order to avoid index surprises.
- **Pop + Insert**: move items while preserving them.
- **Tuple returns**: return helpful info (e.g., removed item, new length) from helper functions.

## 8. Quick Checks
- What happens to indices after `pop(i)`? → Elements to the right shift left by one.
- How do you move an item to the front? → `item = lst.pop(old_idx)` then `lst.insert(0, item)`.
- How do you avoid off-by-one errors? → Re-evaluate indices after each mutation.

## 9. Summary
Use arrays with intent: storyboard the goal, then apply index-aware operations in order. Pop and insert let you reorder without losing data, and re-checking indices after each change prevents off-by-one mistakes.

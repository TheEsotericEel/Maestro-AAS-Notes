# Challenge: Algorithms

## 1. Introduction
This challenge lesson tests your ability to convert real-world tasks into clear, step-by-step algorithms. You'll practice identifying appropriate step granularity, ordering operations logically, and translating algorithms into code.

## 2. Challenge Rounds

### 2.1 Round 1: Morning Coffee Algorithm
**Task**: Create an algorithm for making instant coffee that a robot could follow.

**Solution**:
```
1. Pick up the mug
2. Fill the mug with water
3. Pour the water into the kettle
4. Turn on the kettle
5. Put instant coffee into the mug
6. Pour the hot water into the mug
```

**Analysis**:
- Each step is a single, clear action
- Steps are in logical chronological order
- No assumptions about prior knowledge
- Achieves the goal of making instant coffee

### 2.2 Round 2: Step Granularity Assessment
**Task**: Evaluate if a step is too big, too small, or just right.

**Step**: "Write a friendly email to my manager asking for a day off next week, then open my email app, add their address, write a subject line, and click send."

**Answer**: A) Too big (it should be split into smaller single actions)

**Reasoning**: This step contains multiple distinct actions:
1. Write email content
2. Open email app
3. Add recipient address
4. Write subject line
5. Click send

**Correct Breakdown**:
```
1. Open email app
2. Click "Compose" or "New Email"
3. Add manager's email address
4. Write subject line: "Day Off Request"
5. Write email body requesting day off
6. Click "Send"
```

### 2.3 Round 3: Algorithm Reordering
**Task**: Put jumbled hand-washing steps in correct order.

**Jumbled Steps**:
- Dry your hands with a towel
- Turn on the faucet
- Apply soap to your hands
- Turn off the faucet
- Rinse your hands under the water

**Correct Order**: 2, 3, 5, 1, 4

**Ordered Algorithm**:
```
1. Turn on the faucet
2. Apply soap to your hands
3. Rinse your hands under the water
4. Dry your hands with a towel
5. Turn off the faucet
```

**Logic Verification**:
- Must turn on water before washing
- Soap comes before rinsing
- Rinse before drying
- Can turn off faucet after rinsing (or before drying)

### 2.4 Round 4: Python Code Translation
**Task**: Convert hand-washing algorithm to Python print statements.

**Solution**:
```python
print("1. Turn on the faucet")
print("2. Wet your hands")
print("3. Apply soap")
print("4. Scrub your hands for 20 seconds")
print("5. Rinse your hands")
print("6. Dry your hands")
```

**Code Analysis**:
- Each print statement represents one clear action
- Sequential order matches real-world process
- Numbered steps maintain algorithm structure
- Ready for execution and validation

### 2.5 Round 5: File Management Algorithm
**Task**: Create algorithm for cleaning screenshots from Downloads folder.

**Solution**:
```
1. Open the Downloads folder
2. Search or filter files by type to show only images (PNG, JPG)
3. Sort the results by date modified
4. Select all screenshot files older than 7 days
5. Move the selected files to the Trash
6. Empty the Trash
```

**Algorithm Strengths**:
- **Appropriate Granularity**: Each step is a single logical action
- **Clear Sequence**: Operations must occur in this order
- **Specific Criteria**: Clear conditions for file selection
- **Complete Process**: From start to finish

## 3. Algorithm Design Principles Demonstrated

### 3.1 Step Granularity
**Good Step Characteristics**:
- Single action per step
- No hidden compound operations
- Clear and unambiguous
- Appropriate level of detail

**Examples from Challenges**:
- ✅ "Turn on the kettle" (single action)
- ❌ "Write email and send it" (multiple actions)

### 3.2 Logical Ordering
**Key Principles**:
- Dependencies must be respected
- Precedence relationships matter
- Some steps have flexibility in ordering
- Critical path must be maintained

**Hand Washing Dependencies**:
```
Turn on water → Apply soap → Rinse → Dry → Turn off water
```

### 3.3 Completeness
**Algorithm Must Include**:
- All necessary steps
- Proper initialization
- Clear termination
- Error consideration (advanced)

### 3.4 Clarity
**Requirements**:
- No ambiguous language
- Specific actions, not vague intentions
- Clear start and end points
- No assumptions about context

## 4. Common Algorithm Patterns

### 4.1 Sequential Processing
```
Step 1 → Step 2 → Step 3 → Step 4 → Step 5
```
**Examples**: Morning coffee, hand washing

### 4.2 Selection/Filtering
```
1. Get all items
2. Apply filter criteria
3. Select matching items
4. Process selected items
```
**Example**: Downloads folder cleanup

### 4.3 Preparation → Action → Cleanup
```
1. Setup/Preparation
2. Main Action
3. Cleanup/Termination
```
**Examples**: Cooking, cleaning tasks

## 5. Code Translation Patterns

### 5.1 Simple Print Statements
```python
print("Step description")
```
**Use Case**: Algorithm visualization and debugging

### 5.2 Function-Based Structure
```python
def make_coffee():
    pick_up_mug()
    fill_mug_with_water()
    pour_water_into_kettle()
    turn_on_kettle()
    add_coffee_to_mug()
    pour_hot_water_into_mug()
```

### 5.3 Parameterized Algorithms
```python
def clean_folder(folder_path, file_types, days_old):
    open_folder(folder_path)
    filter_by_type(file_types)
    sort_by_date()
    select_older_than(days_old)
    move_to_trash()
    empty_trash()
```

## 6. Advanced Considerations

### 6.1 Error Handling
```python
def make_coffee():
    try:
        pick_up_mug()
        if kettle_has_water():
            turn_on_kettle()
        else:
            fill_kettle()
            turn_on_kettle()
        add_coffee_to_mug()
        pour_hot_water_into_mug()
    except NoMugError:
        print("No mug available")
    except KettleError:
        print("Kettle not working")
```

### 6.2 Conditional Logic
```python
def clean_downloads():
    open_downloads_folder()
    screenshots = filter_by_type(["PNG", "JPG", "Screenshot"])
    old_files = filter_by_date(screenshots, days=7)
    if len(old_files) > 0:
        move_to_trash(old_files)
        if confirm_empty_trash():
            empty_trash()
```

### 6.3 Loop Structures
```python
def process_all_files():
    files = get_all_files()
    for file in files:
        if is_screenshot(file) and is_older_than(file, 7):
            move_to_trash(file)
    empty_trash()
```

## 7. Algorithm Evaluation Criteria

### 7.1 Correctness
- ✅ Produces desired result
- ✅ Handles all valid inputs
- ✅ Terminates properly

### 7.2 Efficiency
- ✅ Minimal unnecessary steps
- ✅ Optimal ordering
- ✅ Resource consideration

### 7.3 Clarity
- ✅ Easy to understand
- ✅ Well-documented
- ✅ Maintainable

### 7.4 Robustness
- ✅ Error handling
- ✅ Edge case consideration
- ✅ Input validation

## 8. Practice Exercises

### 8.1 Exercise 1: Daily Routine Algorithm
Create an algorithm for "getting ready for bed" with 5-8 steps. Consider:
- Appropriate granularity
- Logical ordering
- Complete coverage

### 8.2 Exercise 2: Granularity Practice
Take these complex steps and break them down:
- "Make a sandwich"
- "Do laundry"
- "Study for an exam"

### 8.3 Exercise 3: Code Translation
Convert your bed routine algorithm to Python using:
- Simple print statements
- Function calls
- Error handling

### 8.4 Exercise 4: Algorithm Improvement
Take a simple algorithm (like making toast) and enhance it with:
- Conditional logic
- Error handling
- Optimization

## 9. Summary

### Key Skills Demonstrated
- **Algorithm Design**: Converting real-world tasks to step-by-step procedures
- **Granularity Control**: Finding the right level of detail
- **Logical Ordering**: Understanding dependencies and sequence
- **Code Translation**: Converting algorithms to executable code
- **Pattern Recognition**: Identifying common algorithm structures

### Core Insights
- **Robot-Ready Steps**: Single, clear actions without assumptions
- **Sequential Logic**: Order matters and dependencies must be respected
- **Complete Coverage**: Algorithms must handle the entire process
- **Code Validation**: Python translation tests algorithm logic

### Next Steps
- Practice with more complex real-world scenarios
- Learn about control structures (if/else, loops)
- Study algorithm complexity and optimization
- Explore data structure integration

## 10. Real-World Applications

### 10.1 Software Development
- **User Story Implementation**: Breaking features into steps
- **Testing Procedures**: Systematic test execution
- **Deployment Scripts**: Automated release processes

### 10.2 Business Processes
- **Workflow Automation**: Streamlining repetitive tasks
- **Quality Assurance**: Systematic checking procedures
- **Training Materials**: Clear instructional guides

### 10.3 Personal Productivity
- **Habit Formation**: Structured daily routines
- **Project Management**: Breaking projects into tasks
- **Learning Systems**: Systematic skill acquisition

> **Challenge Success**: "You've demonstrated the core skill of algorithmic thinking - breaking complex tasks into clear, sequential steps that can be executed without ambiguity."

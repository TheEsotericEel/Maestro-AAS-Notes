# Applying Stacks to Undo Behavior

## 1. Introduction
Undo functionality is one of the most intuitive applications of stack data structures. When users perform actions in an application, each action can be stored in a stack, and undo operations simply pop the most recent actions off the stack. This lesson explores how to implement undo behavior using Python lists as stacks.

## 2. The Text Editor Analogy
### Visualizing Undo with Stacks
Imagine typing in a text editor and using Ctrl+Z (Undo):

```
User Actions Sequence:
Type "H" → Type "i" → Delete "i" → Type "!" → Delete "!"

Stack Representation (Bottom to Top):
┌─────────────┐  ← Top (most recent action)
│  delete !   │
├─────────────┤
│   type !    │
├─────────────┤
│  delete i   │
├─────────────┤
│   type i    │
├─────────────┤
│   type H    │  ← Bottom (first action)
└─────────────┘

Undo Sequence (LIFO):
delete ! → type ! → delete i → type i → type H
```

**The Process**:
1. User types "H" → push "type H" to history stack
2. User types "i" → push "type i" to history stack
3. User deletes "i" → push "delete i" to history stack
4. User hits Undo → pop "delete i" (last action)
5. User hits Undo again → pop "type i" (previous action)

## 3. Basic Undo Implementation
### Action Representation
```python
# Each user action becomes a string in the history stack
history = []

# User types "H"
history.append("type H")
print(f"After typing H: {history}")

# User types "i"  
history.append("type i")
print(f"After typing i: {history}")

# User deletes "i"
history.append("delete i")
print(f"After deleting i: {history}")

# Current history stack
print(f"Full history: {history}")
print(f"Last action: {history[-1]}")
```

### Single Undo Operation
```python
# Implementing one undo operation
history = ["type H", "type i", "delete i"]
print(f"Before undo: {history}")

# Perform undo (pop last action)
last_action = history.pop()
print(f"Undid: {last_action}")
print(f"After undo: {history}")
print(f"New last action: {history[-1] if history else 'None'}")
```

### Multiple Undo Operations
```python
# Multiple undos in sequence
history = ["type H", "type i", "type !", "delete !"]
print(f"Initial: {history}")

# First undo
first_undo = history.pop()
print(f"First undo: {first_undo}")
print(f"After first undo: {history}")

# Second undo
second_undo = history.pop()
print(f"Second undo: {second_undo}")
print(f"After second undo: {history}")

# Remaining actions
print(f"Remaining actions: {history}")
```

## 4. Complete Undo Workflow
### Step-by-Step Example
```python
# Complete undo workflow demonstration
def demonstrate_undo_workflow():
    """Demonstrate full undo workflow"""
    history = []
    
    print("=== User Actions ===")
    # User types "Hello"
    history.append("type Hello")
    print(f"Typed 'Hello': {history}")
    
    # User types "!"
    history.append("type !")
    print(f"Typed '!': {history}")
    
    # User deletes "!"
    history.append("delete !")
    print(f"Deleted '!': {history}")
    
    # User types "?"
    history.append("type ?")
    print(f"Typed '?': {history}")
    
    print("\n=== Undo Operations ===")
    # First undo
    first_undo = history.pop()
    print(f"First undo: {first_undo}")
    print(f"History after first undo: {history}")
    
    # Second undo
    second_undo = history.pop()
    print(f"Second undo: {second_undo}")
    print(f"History after second undo: {history}")
    
    print(f"\nFinal remaining actions: {history}")
    return history

# Run demonstration
final_history = demonstrate_undo_workflow()
```

### Interactive Undo Demo
```python
class UndoHistory:
    """Simple undo history manager"""
    
    def __init__(self):
        self.history = []
    
    def record_action(self, action):
        """Record a user action"""
        self.history.append(action)
        self.display_history(f"Recorded: {action}")
    
    def undo(self):
        """Perform undo operation"""
        if not self.history:
            print("Nothing to undo")
            return None
        
        action = self.history.pop()
        self.display_history(f"Undone: {action}")
        return action
    
    def get_undo_count(self):
        """Get number of possible undos"""
        return len(self.history)
    
    def display_history(self, message):
        """Display current history state"""
        print(f"{message}")
        print(f"History: {self.history}")
        if self.history:
            print(f"Last action: {self.history[-1]}")
        else:
            print("No actions recorded")
        print("-" * 40)

# Usage demonstration
undo_manager = UndoHistory()
undo_manager.record_action("type Hello")
undo_manager.record_action("type !")
undo_manager.record_action("delete !")
undo_manager.record_action("type ?")

undo_manager.undo()  # Undoes "type ?"
undo_manager.undo()  # Undoes "delete !"
undo_manager.undo()  # Undoes "type !"
```

## 5. Advanced Undo Patterns
### Pattern 1: Action with Data
```python
class ActionHistory:
    """History that stores action data"""
    
    def __init__(self):
        self.history = []
    
    def record_action(self, action_type, data):
        """Record action with associated data"""
        action = {
            'type': action_type,
            'data': data,
            'timestamp': len(self.history)
        }
        self.history.append(action)
        print(f"Recorded {action_type}: {data}")
    
    def undo(self):
        """Undo last action"""
        if not self.history:
            print("Nothing to undo")
            return None
        
        action = self.history.pop()
        print(f"Undone {action['type']}: {action['data']}")
        return action
    
    def get_last_action(self):
        """Get last action without removing"""
        if not self.history:
            return None
        
        return self.history[-1]

# Usage
action_history = ActionHistory()
action_history.record_action("type", "Hello")
action_history.record_action("type", "!")
action_history.record_action("delete", "!")

last_action = action_history.get_last_action()
print(f"Last action: {last_action}")

action_history.undo()
action_history.undo()
```

### Pattern 2: Undo with State Restoration
```python
class TextEditorWithUndo:
    """Text editor with full undo functionality"""
    
    def __init__(self):
        self.content = ""
        self.history = []
    
    def type_text(self, text):
        """Type text and save state"""
        # Save current state before change
        self.history.append(self.content)
        self.content += text
        print(f"Typed: '{text}'")
        print(f"Content: '{self.content}'")
    
    def delete_text(self, count=1):
        """Delete characters and save state"""
        # Save current state before change
        self.history.append(self.content)
        self.content = self.content[:-count]
        print(f"Deleted {count} character(s)")
        print(f"Content: '{self.content}'")
    
    def undo(self):
        """Undo last action"""
        if not self.history:
            print("Nothing to undo")
            return
        
        # Restore previous state
        self.content = self.history.pop()
        print(f"Undo successful")
        print(f"Content: '{self.content}'")
    
    def get_content(self):
        """Get current content"""
        return self.content
    
    def get_undo_count(self):
        """Get number of possible undos"""
        return len(self.history)

# Usage
editor = TextEditorWithUndo()
editor.type_text("Hello")
editor.type_text("!")
editor.delete_text(1)  # Delete "!"
editor.type_text("?")

print(f"\nFinal content: '{editor.get_content()}'")
print(f"Possible undos: {editor.get_undo_count()}")

editor.undo()  # Undoes typing "?"
editor.undo()  # Undoes deleting "!"
editor.undo()  # Undoes typing "!"

print(f"\nAfter undos: '{editor.get_content()}'")
```

### Pattern 3: Multi-Level Undo
```python
class MultiLevelUndo:
    """Multi-level undo with action grouping"""
    
    def __init__(self):
        self.history = []
        self.action_groups = []
    
    def start_action_group(self, description):
        """Start a group of related actions"""
        group = {
            'description': description,
            'actions': [],
            'start_time': len(self.history)
        }
        self.action_groups.append(group)
        print(f"Started action group: {description}")
    
    def record_action(self, action):
        """Record action within current group"""
        self.history.append(action)
        if self.action_groups:
            self.action_groups[-1]['actions'].append(action)
        print(f"Recorded: {action}")
    
    def undo_last_action(self):
        """Undo single last action"""
        if not self.history:
            print("Nothing to undo")
            return None
        
        action = self.history.pop()
        print(f"Undid single action: {action}")
        return action
    
    def undo_last_group(self):
        """Undo entire last action group"""
        if not self.action_groups:
            print("No action groups to undo")
            return None
        
        group = self.action_groups.pop()
        undone_actions = []
        
        # Undo all actions in the group
        while self.history and len(self.history) > group['start_time']:
            action = self.history.pop()
            undone_actions.append(action)
        
        print(f"Undid group '{group['description']}' with {len(undone_actions)} actions")
        return undone_actions

# Usage
multi_undo = MultiLevelUndo()
multi_undo.start_action_group("Type greeting")
multi_undo.record_action("type H")
multi_undo.record_action("type e")
multi_undo.record_action("type l")
multi_undo.record_action("type l")
multi_undo.record_action("type o")

multi_undo.start_action_group("Add punctuation")
multi_undo.record_action("type !")
multi_undo.record_action("delete !")
multi_undo.record_action("type ?")

print(f"\nCurrent history: {multi_undo.history}")
multi_undo.undo_last_group()  # Undoes entire punctuation group
print(f"After group undo: {multi_undo.history}")
```

## 6. Real-World Applications
### Application 1: Drawing Program
```python
class DrawingUndo:
    """Undo system for drawing application"""
    
    def __init__(self):
        self.shapes = []
        self.history = []
    
    def add_shape(self, shape_type, position, color):
        """Add a shape to drawing"""
        shape = {
            'type': shape_type,
            'position': position,
            'color': color,
            'id': len(self.shapes)
        }
        
        # Save state before adding
        self.history.append(('add', shape))
        self.shapes.append(shape)
        print(f"Added {shape_type} at {position}")
    
    def remove_shape(self, shape_id):
        """Remove a shape from drawing"""
        # Find shape
        shape = None
        for i, s in enumerate(self.shapes):
            if s['id'] == shape_id:
                shape = self.shapes.pop(i)
                break
        
        if shape:
            # Save state before removing
            self.history.append(('remove', shape))
            print(f"Removed {shape['type']} at {shape['position']}")
    
    def undo(self):
        """Undo last drawing action"""
        if not self.history:
            print("Nothing to undo")
            return
        
        action, shape = self.history.pop()
        
        if action == 'add':
            # Undo adding: remove the shape
            self.shapes = [s for s in self.shapes if s['id'] != shape['id']]
            print(f"Undid adding {shape['type']}")
        elif action == 'remove':
            # Undo removing: add the shape back
            self.shapes.append(shape)
            print(f"Undid removing {shape['type']}")
    
    def get_shapes(self):
        """Get current shapes"""
        return self.shapes

# Usage
drawing = DrawingUndo()
drawing.add_shape("circle", (10, 20), "red")
drawing.add_shape("rectangle", (30, 40), "blue")
drawing.remove_shape(1)  # Remove circle
drawing.add_shape("triangle", (50, 60), "green")

print(f"Current shapes: {drawing.get_shapes()}")
drawing.undo()  # Undo adding triangle
drawing.undo()  # Undo removing circle
print(f"After undos: {drawing.get_shapes()}")
```

### Application 2: Configuration Management
```python
class ConfigUndo:
    """Configuration settings with undo"""
    
    def __init__(self):
        self.settings = {}
        self.history = []
    
    def set_setting(self, key, value):
        """Set a configuration value"""
        # Save old value before change
        old_value = self.settings.get(key)
        self.history.append(('set', key, old_value))
        
        self.settings[key] = value
        print(f"Set {key} = {value}")
    
    def delete_setting(self, key):
        """Delete a configuration setting"""
        if key in self.settings:
            # Save value before deletion
            old_value = self.settings[key]
            self.history.append(('delete', key, old_value))
            
            del self.settings[key]
            print(f"Deleted setting {key}")
    
    def undo(self):
        """Undo last configuration change"""
        if not self.history:
            print("Nothing to undo")
            return
        
        action, key, old_value = self.history.pop()
        
        if action == 'set':
            if old_value is None:
                # Setting didn't exist before
                if key in self.settings:
                    del self.settings[key]
                print(f"Undid setting {key} (restored to not set)")
            else:
                # Restore old value
                self.settings[key] = old_value
                print(f"Undid setting {key} (restored to {old_value})")
        elif action == 'delete':
            # Restore deleted setting
            self.settings[key] = old_value
            print(f"Undid deleting {key} (restored to {old_value})")
    
    def get_settings(self):
        """Get current settings"""
        return self.settings

# Usage
config = ConfigUndo()
config.set_setting("theme", "dark")
config.set_setting("font_size", 14)
config.set_setting("language", "en")
config.delete_setting("font_size")

print(f"Current settings: {config.get_settings()}")
config.undo()  # Undo deleting font_size
config.undo()  # Undo setting language
print(f"After undos: {config.get_settings()}")
```

### Application 3: Game State Management
```python
class GameStateUndo:
    """Game state with undo functionality"""
    
    def __init__(self):
        self.player_pos = [0, 0]
        self.score = 0
        self.items = []
        self.history = []
    
    def move_player(self, dx, dy):
        """Move player position"""
        # Save state before move
        self._save_state()
        
        self.player_pos[0] += dx
        self.player_pos[1] += dy
        print(f"Moved to {self.player_pos}")
    
    def add_score(self, points):
        """Add points to score"""
        # Save state before scoring
        self._save_state()
        
        self.score += points
        print(f"Score: {self.score}")
    
    def collect_item(self, item):
        """Collect an item"""
        # Save state before collection
        self._save_state()
        
        self.items.append(item)
        print(f"Collected: {item}")
    
    def _save_state(self):
        """Save current state to history"""
        state = {
            'pos': self.player_pos.copy(),
            'score': self.score,
            'items': self.items.copy()
        }
        self.history.append(state)
    
    def undo(self):
        """Undo last game action"""
        if not self.history:
            print("Nothing to undo")
            return
        
        # Restore previous state
        state = self.history.pop()
        self.player_pos = state['pos']
        self.score = state['score']
        self.items = state['items']
        print(f"Undid - Position: {self.player_pos}, Score: {self.score}, Items: {self.items}")
    
    def get_state(self):
        """Get current game state"""
        return {
            'position': self.player_pos,
            'score': self.score,
            'items': self.items
        }

# Usage
game = GameStateUndo()
game.move_player(1, 0)
game.add_score(10)
game.collect_item("coin")
game.move_player(0, 1)

print(f"Current state: {game.get_state()}")
game.undo()  # Undo move
game.undo()  # Undo collecting coin
print(f"After undos: {game.get_state()}")
```

## 7. Error Handling and Edge Cases
### Safe Undo Implementation
```python
class SafeUndoHistory:
    """Undo system with comprehensive error handling"""
    
    def __init__(self, max_history=100):
        self.history = []
        self.max_history = max_history
    
    def record_action(self, action):
        """Safely record an action"""
        if len(self.history) >= self.max_history:
            # Remove oldest action to make room
            removed = self.history.pop(0)
            print(f"Removed old action: {removed}")
        
        self.history.append(action)
        print(f"Recorded: {action}")
    
    def undo(self):
        """Safely undo last action"""
        if not self.history:
            print("Error: No actions to undo")
            return None
        
        action = self.history.pop()
        print(f"Undone: {action}")
        return action
    
    def undo_multiple(self, count):
        """Undo multiple actions safely"""
        undone = []
        for i in range(count):
            action = self.undo()
            if action is None:
                break
            undone.append(action)
        
        print(f"Undone {len(undone)} actions")
        return undone
    
    def clear_history(self):
        """Clear all history"""
        count = len(self.history)
        self.history.clear()
        print(f"Cleared {count} actions from history")
    
    def get_history_summary(self):
        """Get summary of history"""
        return {
            'total_actions': len(self.history),
            'max_history': self.max_history,
            'recent_actions': self.history[-5:] if self.history else []
        }

# Usage
safe_undo = SafeUndoHistory(max_history=5)
for i in range(7):
    safe_undo.record_action(f"action_{i}")

print(f"\nHistory summary: {safe_undo.get_history_summary()}")
safe_undo.undo_multiple(3)
```

## 8. Performance Considerations
### Memory Management
```python
import sys

class EfficientUndo:
    """Memory-efficient undo system"""
    
    def __init__(self, max_memory_mb=10):
        self.history = []
        self.max_memory = max_memory_mb * 1024 * 1024  # Convert to bytes
    
    def _estimate_memory_usage(self):
        """Estimate current memory usage"""
        return sys.getsizeof(self.history)
    
    def record_action(self, action):
        """Record action with memory management"""
        # Check memory usage
        current_memory = self._estimate_memory_usage()
        
        if current_memory > self.max_memory:
            # Remove oldest actions until under limit
            while self.history and self._estimate_memory_usage() > self.max_memory:
                removed = self.history.pop(0)
                print(f"Removed old action due to memory limit: {removed}")
        
        self.history.append(action)
    
    def undo(self):
        """Standard undo operation"""
        if not self.history:
            return None
        
        return self.history.pop()
    
    def get_memory_info(self):
        """Get memory usage information"""
        current = self._estimate_memory_usage()
        return {
            'current_bytes': current,
            'current_mb': current / (1024 * 1024),
            'max_mb': self.max_memory / (1024 * 1024),
            'usage_percent': (current / self.max_memory) * 100
        }

# Usage
efficient = EfficientUndo(max_memory_mb=1)
for i in range(1000):
    efficient.record_action(f"action_{i}")

print(f"Memory info: {efficient.get_memory_info()}")
```

### Time Complexity Analysis
```python
import time

def measure_undo_performance():
    """Measure performance of undo operations"""
    history_sizes = [100, 1000, 10000, 100000]
    
    for size in history_sizes:
        # Build history
        history = [f"action_{i}" for i in range(size)]
        
        # Measure undo performance
        start_time = time.time()
        for _ in range(min(1000, size // 10)):  # Don't undo more than we have
            if history:
                history.pop()
        undo_time = time.time() - start_time
        
        print(f"History size: {size:,}")
        print(f"Undo operations: {min(1000, size // 10):,}")
        print(f"Time: {undo_time:.4f} seconds")
        print(f"Average per undo: {(undo_time / min(1000, size // 10)) * 1000:.2f} ms")
        print("-" * 40)

# Run performance test
measure_undo_performance()
```

## 9. Common Patterns and Techniques
### Pattern 1: Command Pattern with Undo
```python
class Command:
    """Base command class with undo capability"""
    
    def __init__(self, description):
        self.description = description
    
    def execute(self):
        """Execute the command"""
        raise NotImplementedError
    
    def undo(self):
        """Undo the command"""
        raise NotImplementedError

class TypeCommand(Command):
    """Command for typing text"""
    
    def __init__(self, editor, text):
        super().__init__(f"type '{text}'")
        self.editor = editor
        self.text = text
    
    def execute(self):
        self.editor.content += self.text
        print(f"Executed: {self.description}")
    
    def undo(self):
        self.editor.content = self.editor.content[:-len(self.text)]
        print(f"Undid: {self.description}")

class DeleteCommand(Command):
    """Command for deleting text"""
    
    def __init__(self, editor, count=1):
        super().__init__(f"delete {count} character(s)")
        self.editor = editor
        self.count = count
        self.deleted_text = ""
    
    def execute(self):
        self.deleted_text = self.editor.content[-self.count:]
        self.editor.content = self.editor.content[:-self.count]
        print(f"Executed: {self.description}")
    
    def undo(self):
        self.editor.content += self.deleted_text
        print(f"Undid: {self.description}")

class CommandEditor:
    """Editor using command pattern with undo"""
    
    def __init__(self):
        self.content = ""
        self.history = []
    
    def execute_command(self, command):
        """Execute and record command"""
        command.execute()
        self.history.append(command)
    
    def undo(self):
        """Undo last command"""
        if not self.history:
            print("Nothing to undo")
            return
        
        command = self.history.pop()
        command.undo()

# Usage
editor = CommandEditor()
editor.execute_command(TypeCommand(editor, "Hello"))
editor.execute_command(TypeCommand(editor, "!"))
editor.execute_command(DeleteCommand(editor, 1))
editor.execute_command(TypeCommand(editor, "?"))

print(f"Content: '{editor.content}'")
editor.undo()
editor.undo()
print(f"After undos: '{editor.content}'")
```

### Pattern 2: Memento Pattern with Undo
```python
class TextEditorMemento:
    """Memento for saving editor state"""
    
    def __init__(self, content, cursor_pos):
        self.content = content
        self.cursor_pos = cursor_pos
    
    def get_content(self):
        return self.content
    
    def get_cursor_pos(self):
        return self.cursor_pos

class TextEditorWithMemento:
    """Editor using memento pattern for undo"""
    
    def __init__(self):
        self.content = ""
        self.cursor_pos = 0
        self.history = []
    
    def type_text(self, text):
        """Save state and type text"""
        self._save_state()
        self.content += text
        self.cursor_pos += len(text)
        print(f"Typed: '{text}'")
    
    def delete_text(self, count=1):
        """Save state and delete text"""
        self._save_state()
        start_pos = max(0, self.cursor_pos - count)
        self.content = self.content[:start_pos] + self.content[self.cursor_pos:]
        self.cursor_pos = start_pos
        print(f"Deleted {count} character(s)")
    
    def _save_state(self):
        """Save current state as memento"""
        memento = TextEditorMemento(self.content, self.cursor_pos)
        self.history.append(memento)
    
    def undo(self):
        """Restore previous state"""
        if not self.history:
            print("Nothing to undo")
            return
        
        memento = self.history.pop()
        self.content = memento.get_content()
        self.cursor_pos = memento.get_cursor_pos()
        print(f"Undo successful")
    
    def get_state(self):
        """Get current state"""
        return f"Content: '{self.content}', Cursor: {self.cursor_pos}"

# Usage
memento_editor = TextEditorWithMemento()
memento_editor.type_text("Hello")
memento_editor.type_text("!")
memento_editor.delete_text(1)
memento_editor.type_text("?")

print(f"Final state: {memento_editor.get_state()}")
memento.undo()
memento.undo()
print(f"After undos: {memento_editor.get_state()}")
```

## 10. Quick Checks
- How do you record an action for undo? → `history.append(action)`
- How do you implement undo? → `history.pop()`
- What does multiple undos mean? → Multiple `pop()` calls
- What happens if you undo too much? → Empty history stack
- Why use stacks for undo? → LIFO matches undo behavior
- Can undo restore previous state? → Yes, with proper action storage

## 11. Summary
Applying stacks to undo behavior demonstrates one of the most practical uses of stack data structures:

### Core Concept
- **Action Recording**: Each user action is pushed onto history stack
- **Undo Operation**: Each undo pops the most recent action
- **LIFO Behavior**: Last action performed is first action undone
- **State Management**: Stack maintains chronological action order

### Implementation Patterns
- **Simple History**: Store action descriptions as strings
- **Rich Actions**: Store action objects with data and undo methods
- **State Snapshots**: Save complete application state for each action
- **Command Pattern**: Encapsulate actions as executable/undoable objects

### Key Advantages
- **Intuitive Behavior**: Matches user expectations for undo
- **Simple Implementation**: Basic stack operations handle everything
- **Memory Efficient**: Only stores what's needed for undo
- **Scalable**: Can handle complex undo scenarios

### Real-World Applications
- **Text Editors**: Typing, deleting, formatting operations
- **Drawing Programs**: Shape creation, modification, deletion
- **Configuration Systems**: Settings changes and preferences
- **Game Development**: Player actions and state changes

### Advanced Features
- **Multi-Level Undo**: Group related actions together
- **Redo Functionality**: Use second stack for redo operations
- **Memory Management**: Limit history size to prevent memory issues
- **Performance Optimization**: Efficient state saving and restoration

> **Key Insight**: "Undo is the perfect real-world example of stacks in action - every action you take gets pushed onto a stack, and every Ctrl+Z just pops the last one off. It's so natural that most users don't even realize they're using a data structure."

### Mastery Checklist
- ✅ Understand action-to-stack mapping
- ✅ Implement basic undo with `pop()`
- ✅ Handle multiple consecutive undos
- ✅ Store rich action data for complex undos
- ✅ Apply to real-world scenarios
- ✅ Handle edge cases (empty history, memory limits)
- ✅ Implement advanced patterns (commands, mementos)
- ✅ Optimize for performance and memory usage
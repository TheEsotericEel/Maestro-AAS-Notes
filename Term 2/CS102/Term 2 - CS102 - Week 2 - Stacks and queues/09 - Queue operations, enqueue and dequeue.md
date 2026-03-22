# Queue operations, enqueue and dequeue

## 1. Introduction
Queue operations are the fundamental actions that make queues work as ordered, fair data structures. The two primary operations are **enqueue** (adding items to the back) and **dequeue** (removing items from the front). This lesson explores these operations in detail, showing how to implement them using Python lists and understanding their behavior through practical examples.

## 2. The Photo Booth Line Analogy
### Visualizing Queue Operations
Imagine a line of people waiting for a photo booth 🎞️:

```
Photo Booth Line (Queue):

Initial: []
Enqueue "Alice": [Alice]
Enqueue "Bob":   [Alice, Bob]
Enqueue "Charlie": [Alice, Bob, Charlie]

Dequeue: Alice leaves → [Bob, Charlie]
Dequeue: Bob leaves → [Charlie]
Dequeue: Charlie leaves → []
```

**Queue Operations Mapping**:
- **New people join at the back** → enqueue operation
- **Next person served from the front** → dequeue operation
- **Order preserved** → first in, first out

### Core Operations Concept
```python
# Queue operations using Python list
queue = []

# Enqueue (add to back)
queue.append("Alice")    # Queue: ["Alice"]
queue.append("Bob")      # Queue: ["Alice", "Bob"]
queue.append("Charlie")  # Queue: ["Alice", "Bob", "Charlie"]

# Dequeue (remove from front)
served = queue.pop(0)    # served = "Alice", Queue: ["Bob", "Charlie"]
served = queue.pop(0)    # served = "Bob", Queue: ["Charlie"]
served = queue.pop(0)    # served = "Charlie", Queue: []
```

## 3. Enqueue Operation
### Adding Items to the Queue
**Enqueue** means adding an item to the back of the queue:

```python
# Basic enqueue operation
queue = []

print(f"Initial queue: {queue}")

# Enqueue first item
queue.append("Alice")
print(f"After enqueue 'Alice': {queue}")

# Enqueue second item
queue.append("Bob")
print(f"After enqueue 'Bob': {queue}")

# Enqueue third item
queue.append("Charlie")
print(f"After enqueue 'Charlie': {queue}")

# Queue state after all enqueues
print(f"Final queue: {queue}")
print(f"Queue size: {len(queue)}")
print(f"Front item: {queue[0]}")
print(f"Back item: {queue[-1]}")
```

### Enqueue Characteristics
- **Location**: Always adds to the back (right end) of the list
- **Method**: Uses `list.append(item)` in Python
- **Time Complexity**: O(1) - constant time operation
- **Order Impact**: New items become the last to be served
- **Queue Growth**: Queue size increases by 1

### Enqueue Workflow
```python
def demonstrate_enqueue_workflow():
    """Show step-by-step enqueue process"""
    queue = []
    items = ["Alice", "Bob", "Charlie", "David"]
    
    print("=== Enqueue Workflow ===")
    for i, item in enumerate(items, 1):
        queue.append(item)
        print(f"Step {i}: Enqueue '{item}'")
        print(f"  Queue: {queue}")
        print(f"  Front: {queue[0]}, Back: {queue[-1]}")
        print(f"  Size: {len(queue)}")
        print()

# Run demonstration
demonstrate_enqueue_workflow()
```

## 4. Dequeue Operation
### Removing Items from the Queue
**Dequeue** means removing the item from the front of the queue:

```python
# Basic dequeue operation
queue = ["Alice", "Bob", "Charlie"]

print(f"Initial queue: {queue}")

# Dequeue first item
served = queue.pop(0)
print(f"Dequeued: {served}")
print(f"Queue after dequeue: {queue}")

# Dequeue second item
served = queue.pop(0)
print(f"Dequeued: {served}")
print(f"Queue after dequeue: {queue}")

# Dequeue third item
served = queue.pop(0)
print(f"Dequeued: {served}")
print(f"Queue after dequeue: {queue}")
print(f"Is queue empty: {len(queue) == 0}")
```

### Dequeue Characteristics
- **Location**: Always removes from the front (index 0) of the list
- **Method**: Uses `list.pop(0)` in Python
- **Time Complexity**: O(n) - linear time (all items shift left)
- **Order Impact**: Next item becomes the new front
- **Queue Shrink**: Queue size decreases by 1

### Dequeue Workflow
```python
def demonstrate_dequeue_workflow():
    """Show step-by-step dequeue process"""
    queue = ["Alice", "Bob", "Charlie", "David"]
    
    print("=== Dequeue Workflow ===")
    step = 1
    while queue:
        served = queue.pop(0)
        print(f"Step {step}: Dequeue '{served}'")
        print(f"  Served: {served}")
        print(f"  Queue: {queue}")
        if queue:
            print(f"  New front: {queue[0]}")
        print(f"  Size: {len(queue)}")
        print()
        step += 1

# Run demonstration
demonstrate_dequeue_workflow()
```

## 5. Complete Queue Operations Example
### Enqueue and Dequeue Together
```python
def complete_queue_example():
    """Demonstrate both enqueue and dequeue operations"""
    queue = []
    
    print("=== Complete Queue Operations ===")
    
    # Enqueue phase
    print("--- Enqueue Phase ---")
    customers = ["Alice", "Bob", "Charlie"]
    for customer in customers:
        queue.append(customer)
        print(f"Enqueued: {customer}")
        print(f"Queue: {queue}")
    
    print(f"\nQueue ready for service: {queue}")
    
    # Dequeue phase
    print("\n--- Dequeue Phase ---")
    while queue:
        served = queue.pop(0)
        print(f"Served: {served}")
        print(f"Remaining queue: {queue}")
        if queue:
            print(f"Next to serve: {queue[0]}")
        print()
    
    print("All customers served!")

# Run complete example
complete_queue_example()
```

### Interactive Queue Simulation
```python
class InteractiveQueue:
    """Interactive queue demonstration"""
    
    def __init__(self, name):
        self.name = name
        self.items = []
        self.served_count = 0
    
    def enqueue(self, item):
        """Add item to queue"""
        self.items.append(item)
        print(f"[{self.name}] Enqueued: {item}")
        self._display_status()
    
    def dequeue(self):
        """Remove and return front item"""
        if not self.is_empty():
            item = self.items.pop(0)
            self.served_count += 1
            print(f"[{self.name}] Dequeued: {item}")
            self._display_status()
            return item
        else:
            print(f"[{self.name}] Queue is empty - cannot dequeue")
            return None
    
    def peek_front(self):
        """Look at front item without removing"""
        if not self.is_empty():
            return self.items[0]
        return None
    
    def is_empty(self):
        """Check if queue is empty"""
        return len(self.items) == 0
    
    def _display_status(self):
        """Display current queue status"""
        front = self.items[0] if self.items else "None"
        back = self.items[-1] if self.items else "None"
        print(f"  Status: Front={front}, Back={back}, Size={len(self.items)}")
        print(f"  Queue: {self.items}")
        print(f"  Total served: {self.served_count}")

# Usage demonstration
photo_queue = InteractiveQueue("Photo Booth")
photo_queue.enqueue("Alice")
photo_queue.enqueue("Bob")
photo_queue.enqueue("Charlie")
photo_queue.dequeue()
photo_queue.dequeue()
photo_queue.dequeue()
```

## 6. Queue Operation Patterns
### Pattern 1: Service Line Simulation
```python
class ServiceLine:
    """Simulate a service line using queue operations"""
    
    def __init__(self, service_name):
        self.service_name = service_name
        self.queue = []
        self.current_ticket = 1
        self.serving_ticket = 0
    
    def customer_arrives(self, customer_name):
        """Customer joins the line"""
        ticket = self.current_ticket
        customer = {
            'ticket': ticket,
            'name': customer_name,
            'arrival_time': len(self.queue)
        }
        self.queue.append(customer)
        print(f"{customer_name} took ticket #{ticket}")
        self.current_ticket += 1
        return ticket
    
    def serve_next_customer(self):
        """Serve the next customer in line"""
        if not self.queue:
            print(f"No customers waiting at {self.service_name}")
            return None
        
        customer = self.queue.pop(0)
        self.serving_ticket = customer['ticket']
        print(f"Now serving ticket #{customer['ticket']}: {customer['name']}")
        return customer
    
    def get_waiting_list(self):
        """Get list of waiting customers"""
        return [f"#{c['ticket']}: {c['name']}" for c in self.queue]
    
    def get_status(self):
        """Get current service status"""
        if self.queue:
            next_customer = self.queue[0]
            return f"Next: #{next_customer['ticket']} {next_customer['name']}, Waiting: {len(self.queue)}"
        return "No customers waiting"

# Usage
bank_line = ServiceLine("Bank")
bank_line.customer_arrives("Alice Smith")
bank_line.customer_arrives("Bob Johnson")
bank_line.customer_arrives("Charlie Brown")

print(f"Status: {bank_line.get_status()}")
bank_line.serve_next_customer()  # Serves Alice
print(f"Status: {bank_line.get_status()}")
bank_line.serve_next_customer()  # Serves Bob
```

### Pattern 2: Task Processing Queue
```python
class TaskProcessor:
    """Process tasks using queue operations"""
    
    def __init__(self):
        self.task_queue = []
        self.completed_tasks = []
        self.task_id = 1
    
    def add_task(self, task_description, priority="normal"):
        """Add a task to the processing queue"""
        task = {
            'id': self.task_id,
            'description': task_description,
            'priority': priority,
            'added_time': len(self.task_queue)
        }
        self.task_queue.append(task)
        print(f"Task #{task['id']}: '{task_description}' added to queue")
        self.task_id += 1
        return task
    
    def process_next_task(self):
        """Process the next task in the queue"""
        if not self.task_queue:
            print("No tasks to process")
            return None
        
        task = self.task_queue.pop(0)
        task['completed_time'] = len(self.completed_tasks)
        self.completed_tasks.append(task)
        print(f"Processed Task #{task['id']}: '{task['description']}'")
        return task
    
    def get_queue_status(self):
        """Get current queue status"""
        if not self.task_queue:
            return "No tasks waiting"
        
        next_task = self.task_queue[0]
        return f"Next: Task #{next_task['id']} ('{next_task['description']}'), Waiting: {len(self.task_queue)}"
    
    def get_productivity_report(self):
        """Get productivity report"""
        return {
            'tasks_completed': len(self.completed_tasks),
            'tasks_waiting': len(self.task_queue),
            'completion_rate': len(self.completed_tasks) / (len(self.completed_tasks) + len(self.task_queue)) * 100 if (len(self.completed_tasks) + len(self.task_queue)) > 0 else 0
        }

# Usage
processor = TaskProcessor()
processor.add_task("Backup database")
processor.add_task("Send emails")
processor.add_task("Generate reports")

print(f"Status: {processor.get_queue_status()}")
processor.process_next_task()  # Processes backup
processor.process_next_task()  # Processes emails
print(f"Status: {processor.get_queue_status()}")
print(f"Report: {processor.get_productivity_report()}")
```

### Pattern 3: Message Queue System
```python
class MessageQueue:
    """Message passing system using queue operations"""
    
    def __init__(self):
        self.messages = []
        self.processed_messages = []
        self.message_id = 1
    
    def send_message(self, sender, recipient, content):
        """Send a message to the queue"""
        message = {
            'id': self.message_id,
            'sender': sender,
            'recipient': recipient,
            'content': content,
            'timestamp': len(self.messages),
            'status': 'pending'
        }
        self.messages.append(message)
        print(f"Message #{message['id']}: {sender} → {recipient}: '{content}'")
        self.message_id += 1
        return message
    
    def process_next_message(self):
        """Process the next message in the queue"""
        if not self.messages:
            print("No messages to process")
            return None
        
        message = self.messages.pop(0)
        message['status'] = 'delivered'
        message['processed_time'] = len(self.processed_messages)
        self.processed_messages.append(message)
        print(f"Delivered Message #{message['id']}: {message['sender']} → {message['recipient']}")
        return message
    
    def get_message_summary(self):
        """Get message processing summary"""
        return {
            'pending_messages': len(self.messages),
            'delivered_messages': len(self.processed_messages),
            'next_message': self.messages[0] if self.messages else None
        }

# Usage
msg_queue = MessageQueue()
msg_queue.send_message("Alice", "Bob", "Hello Bob!")
msg_queue.send_message("Bob", "Charlie", "Hey Charlie!")
msg_queue.send_message("Charlie", "Alice", "Hi Alice!")

print(f"Summary: {msg_queue.get_message_summary()}")
msg_queue.process_next_message()  # Delivers Alice→Bob message
msg_queue.process_next_message()  # Delivers Bob→Charlie message
print(f"Summary: {msg_queue.get_message_summary()}")
```

## 7. Queue Operation Edge Cases
### Handling Empty Queue
```python
class SafeQueue:
    """Queue with proper error handling"""
    
    def __init__(self):
        self.items = []
    
    def enqueue(self, item):
        """Safely add item to queue"""
        self.items.append(item)
        print(f"Enqueued: {item}")
    
    def dequeue(self):
        """Safely remove item from queue"""
        if self.is_empty():
            print("Warning: Cannot dequeue from empty queue")
            return None
        
        item = self.items.pop(0)
        print(f"Dequeued: {item}")
        return item
    
    def is_empty(self):
        """Check if queue is empty"""
        return len(self.items) == 0
    
    def safe_peek(self):
        """Safely look at front item"""
        if self.is_empty():
            print("Warning: Cannot peek at empty queue")
            return None
        
        return self.items[0]

# Demonstrate edge cases
safe_queue = SafeQueue()

# Try to dequeue from empty queue
safe_queue.dequeue()

# Add items and dequeue normally
safe_queue.enqueue("Item 1")
safe_queue.enqueue("Item 2")
safe_queue.dequeue()
safe_queue.dequeue()

# Try to dequeue from empty queue again
safe_queue.dequeue()
```

### Queue Capacity Management
```python
class BoundedQueue:
    """Queue with maximum capacity limits"""
    
    def __init__(self, max_capacity):
        self.max_capacity = max_capacity
        self.items = []
    
    def enqueue(self, item):
        """Add item if queue not at capacity"""
        if self.is_full():
            print(f"Error: Queue at capacity ({self.max_capacity}) - cannot enqueue {item}")
            return False
        
        self.items.append(item)
        print(f"Enqueued: {item} (capacity: {len(self.items)}/{self.max_capacity})")
        return True
    
    def dequeue(self):
        """Remove item from queue"""
        if self.is_empty():
            print("Error: Cannot dequeue from empty queue")
            return None
        
        item = self.items.pop(0)
        print(f"Dequeued: {item} (capacity: {len(self.items)}/{self.max_capacity})")
        return item
    
    def is_full(self):
        """Check if queue is at capacity"""
        return len(self.items) >= self.max_capacity
    
    def is_empty(self):
        """Check if queue is empty"""
        return len(self.items) == 0
    
    def get_capacity_info(self):
        """Get capacity information"""
        return {
            'current_size': len(self.items),
            'max_capacity': self.max_capacity,
            'available_slots': self.max_capacity - len(self.items),
            'is_full': self.is_full(),
            'is_empty': self.is_empty()
        }

# Usage
limited_queue = BoundedQueue(max_capacity=3)
print(f"Capacity info: {limited_queue.get_capacity_info()}")

limited_queue.enqueue("Item 1")
limited_queue.enqueue("Item 2")
limited_queue.enqueue("Item 3")
limited_queue.enqueue("Item 4")  # Should fail - queue full

limited_queue.dequeue()
limited_queue.enqueue("Item 4")  # Should succeed - space available
print(f"Capacity info: {limited_queue.get_capacity_info()}")
```

## 8. Performance Considerations
### Time Complexity Analysis
```python
import time

def analyze_queue_performance():
    """Analyze performance of queue operations"""
    sizes = [100, 1000, 10000]
    
    print("=== Queue Performance Analysis ===")
    
    for size in sizes:
        # Test enqueue performance
        queue = []
        start_time = time.time()
        for i in range(size):
            queue.append(f"item_{i}")  # Enqueue - O(1)
        enqueue_time = time.time() - start_time
        
        # Test dequeue performance
        start_time = time.time()
        for i in range(min(100, size)):  # Don't empty the queue completely
            if queue:
                queue.pop(0)  # Dequeue - O(n)
        dequeue_time = time.time() - start_time
        
        print(f"Queue size: {size:,}")
        print(f"Enqueue {size:,} items: {enqueue_time:.4f} seconds")
        print(f"Dequeue {min(100, size):,} items: {dequeue_time:.4f} seconds")
        print(f"Average enqueue: {(enqueue_time / size) * 1000:.2f} ms")
        print(f"Average dequeue: {(dequeue_time / min(100, size)) * 1000:.2f} ms")
        print("-" * 50)

# Run performance analysis
analyze_queue_performance()
```

### Efficient Queue Alternative
```python
from collections import deque

class EfficientQueue:
    """High-performance queue using deque"""
    
    def __init__(self):
        self.items = deque()
    
    def enqueue(self, item):
        """Add item to queue - O(1)"""
        self.items.append(item)
        print(f"Enqueued: {item}")
    
    def dequeue(self):
        """Remove item from queue - O(1)"""
        if not self.is_empty():
            item = self.items.popleft()
            print(f"Dequeued: {item}")
            return item
        print("Queue is empty - cannot dequeue")
        return None
    
    def is_empty(self):
        """Check if queue is empty"""
        return len(self.items) == 0
    
    def size(self):
        """Get queue size"""
        return len(self.items)

def compare_queue_implementations():
    """Compare list vs deque queue performance"""
    operations = 10000
    
    # List implementation
    list_queue = []
    start_time = time.time()
    for i in range(operations):
        list_queue.append(f"item_{i}")  # Enqueue
    for i in range(operations):
        if list_queue:
            list_queue.pop(0)  # Dequeue - O(n)
    list_time = time.time() - start_time
    
    # Deque implementation
    deque_queue = deque()
    start_time = time.time()
    for i in range(operations):
        deque_queue.append(f"item_{i}")  # Enqueue
    for i in range(operations):
        if deque_queue:
            deque_queue.popleft()  # Dequeue - O(1)
    deque_time = time.time() - start_time
    
    print("=== Queue Implementation Comparison ===")
    print(f"List queue time: {list_time:.4f} seconds")
    print(f"Deque queue time: {deque_time:.4f} seconds")
    print(f"Performance improvement: {list_time / deque_time:.2f}x faster")

# Run comparison
compare_queue_implementations()
```

## 9. Common Queue Operation Patterns
### Pattern 1: Batch Processing
```python
class BatchProcessor:
    """Process items in batches using queue operations"""
    
    def __init__(self, batch_size=5):
        self.queue = []
        self.batch_size = batch_size
        self.processed_batches = 0
    
    def add_items(self, items):
        """Add multiple items to queue"""
        for item in items:
            self.queue.append(item)
        print(f"Added {len(items)} items to queue")
    
    def process_batch(self):
        """Process next batch of items"""
        if self.is_empty():
            print("No items to process")
            return []
        
        batch = []
        items_to_process = min(self.batch_size, len(self.queue))
        
        for _ in range(items_to_process):
            if self.queue:
                item = self.queue.pop(0)
                batch.append(item)
        
        self.processed_batches += 1
        print(f"Processed batch #{self.processed_batches}: {batch}")
        return batch
    
    def is_empty(self):
        """Check if queue is empty"""
        return len(self.queue) == 0
    
    def get_status(self):
        """Get processing status"""
        return {
            'items_waiting': len(self.queue),
            'batch_size': self.batch_size,
            'processed_batches': self.processed_batches,
            'next_batch_size': min(self.batch_size, len(self.queue))
        }

# Usage
batch_processor = BatchProcessor(batch_size=3)
batch_processor.add_items(["A", "B", "C", "D", "E", "F", "G", "H"])

print(f"Status: {batch_processor.get_status()}")
batch_processor.process_batch()  # Processes A, B, C
batch_processor.process_batch()  # Processes D, E, F
batch_processor.process_batch()  # Processes G, H
print(f"Status: {batch_processor.get_status()}")
```

### Pattern 2: Priority Queue Simulation
```python
class SimplePriorityQueue:
    """Simple priority queue using multiple regular queues"""
    
    def __init__(self):
        self.high_priority = []
        self.normal_priority = []
        self.low_priority = []
    
    def enqueue(self, item, priority="normal"):
        """Add item with priority"""
        if priority == "high":
            self.high_priority.append(item)
            print(f"High priority enqueue: {item}")
        elif priority == "normal":
            self.normal_priority.append(item)
            print(f"Normal priority enqueue: {item}")
        elif priority == "low":
            self.low_priority.append(item)
            print(f"Low priority enqueue: {item}")
        else:
            print(f"Unknown priority: {priority}")
    
    def dequeue(self):
        """Remove highest priority item"""
        # Check high priority first
        if self.high_priority:
            item = self.high_priority.pop(0)
            print(f"Dequeued high priority: {item}")
            return item
        
        # Then normal priority
        if self.normal_priority:
            item = self.normal_priority.pop(0)
            print(f"Dequeued normal priority: {item}")
            return item
        
        # Finally low priority
        if self.low_priority:
            item = self.low_priority.pop(0)
            print(f"Dequeued low priority: {item}")
            return item
        
        print("All queues empty")
        return None
    
    def get_status(self):
        """Get queue status"""
        return {
            'high_priority': len(self.high_priority),
            'normal_priority': len(self.normal_priority),
            'low_priority': len(self.low_priority),
            'total_items': len(self.high_priority) + len(self.normal_priority) + len(self.low_priority)
        }

# Usage
priority_queue = SimplePriorityQueue()
priority_queue.enqueue("Urgent task", "high")
priority_queue.enqueue("Regular task", "normal")
priority_queue.enqueue("Background task", "low")
priority_queue.enqueue("Emergency fix", "high")

print(f"Status: {priority_queue.get_status()}")
priority_queue.dequeue()  # Processes Urgent task
priority_queue.dequeue()  # Processes Emergency fix
priority_queue.dequeue()  # Processes Regular task
priority_queue.dequeue()  # Processes Background task
```

## 10. Quick Checks
- What does enqueue do? → Adds item to the back of the queue
- What does dequeue do? → Removes item from the front of the queue
- Which Python method is used for enqueue? → `append()`
- Which Python method is used for dequeue? → `pop(0)`
- What's the time complexity of enqueue? → O(1)
- What's the time complexity of dequeue with lists? → O(n)
- How can you make dequeue more efficient? → Use `collections.deque`
- What happens if you dequeue from an empty queue? → Error/exception

## 11. Summary
Queue operations are the fundamental actions that make queues work as ordered, fair data structures:

### Core Operations
- **Enqueue**: Add item to the back of the queue using `append()`
- **Dequeue**: Remove item from the front of the queue using `pop(0)`
- **FIFO Behavior**: First item in is first item out
- **Order Preservation**: Input order exactly matches output order

### Implementation Details
- **Python List**: Natural queue representation with `append()` and `pop(0)`
- **Enqueue Complexity**: O(1) - constant time operation
- **Dequeue Complexity**: O(n) - linear time with lists (all items shift)
- **Efficient Alternative**: Use `collections.deque` for O(1) dequeue

### Operation Characteristics
| Operation | Python Method | Location | Time Complexity | Purpose |
|-----------|---------------|----------|-----------------|---------|
| Enqueue | `append(item)` | Back (right end) | O(1) | Add new item |
| Dequeue | `pop(0)` | Front (index 0) | O(n) | Remove next item |
| Peek | `queue[0]` | Front (index 0) | O(1) | Look at next item |
| Size | `len(queue)` | N/A | O(1) | Get queue size |
| Empty Check | `len(queue) == 0` | N/A | O(1) | Check if empty |

### Common Patterns
- **Service Lines**: Customers waiting in order
- **Task Processing**: Jobs processed in arrival order
- **Message Passing**: Communications delivered sequentially
- **Batch Processing**: Groups of items processed together

### Edge Cases and Safety
- **Empty Queue**: Always check before dequeuing
- **Capacity Limits**: Handle maximum queue size constraints
- **Error Handling**: Graceful handling of invalid operations
- **Performance**: Consider deque for high-volume queues

### Real-World Applications
- **Customer Service**: People waiting in lines
- **Print Management**: Documents waiting to print
- **Network Packets**: Data waiting to be processed
- **Task Scheduling**: Jobs waiting for CPU time

> **Key Insight**: "Queue operations are simple but powerful - enqueue adds to the back, dequeue removes from the front, and together they create perfect fairness. The beauty is in the simplicity: first in, first out, every single time."

### Mastery Checklist
- ✅ Understand enqueue operation and implementation
- ✅ Understand dequeue operation and implementation
- ✅ Use Python list methods for queue operations
- ✅ Handle empty queue edge cases
- ✅ Recognize performance characteristics
- ✅ Apply queue operations to real problems
- ✅ Choose efficient implementations when needed
- ✅ Implement safe queue operations
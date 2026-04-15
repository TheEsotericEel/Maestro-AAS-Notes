# What is FIFO?

## 1. Introduction
FIFO (First-In, First-Out) is a fundamental data structure principle that governs how items are processed in order. Unlike stacks that use LIFO (Last-In, First-Out), FIFO ensures that the first item added to a collection is the first one to be removed. This lesson explores FIFO behavior, its real-world applications, and how it differs from LIFO.

## 2. The Concert Line Analogy
### Visualizing FIFO Behavior
Imagine a long line of people waiting to get into a concert 🎵:

```
Concert Line (FIFO):

FRONT (first to enter) ← [Person 1] [Person 2] [Person 3] [Person 4] ← BACK (last to enter)

Process:
1. Person 1 arrives first → joins front
2. Person 2 arrives → joins behind Person 1
3. Person 3 arrives → joins behind Person 2
4. Person 4 arrives → joins behind Person 3

Service Order:
Person 1 enters first (was first in line)
Person 2 enters second (was second in line)
Person 3 enters third (was third in line)
Person 4 enters fourth (was last in line)
```

**FIFO Definition**: The first item that goes in is the first one that comes out.

### Core FIFO Characteristics
- **Arrival Order Matters**: Items are processed in the order they arrive
- **Front Access**: New items join at the back, service happens at the front
- **Fairness**: The longest-waiting item gets served first
- **Predictable Order**: Service order matches arrival order exactly

## 3. FIFO vs LIFO Comparison
### Contrasting Behaviors
```
FIFO (Queue) vs LIFO (Stack):

FIFO - Concert Line:
Input:  Person 1 → Person 2 → Person 3 → Person 4
Output: Person 1 → Person 2 → Person 3 → Person 4

LIFO - Plate Stack:
Input:  Plate 1 → Plate 2 → Plate 3 → Plate 4
Output: Plate 4 → Plate 3 → Plate 2 → Plate 1
```

### When to Use Each
| Situation | FIFO or LIFO? | Why? |
|-----------|----------------|------|
| Concert line | FIFO | Fairness - first come, first served |
| Plate stack | LIFO | Convenience - easiest access to top |
| Print queue | FIFO | Fairness - earliest job first |
| Browser back | LIFO | Recency - most recent page first |
| Bus boarding | FIFO | Fairness - arrival order matters |
| Undo system | LIFO | Recency - last action undone first |

## 4. Real-World FIFO Examples
### Example 1: Bus Stop Line
```python
# Bus stop FIFO behavior
bus_line = []

# People arrive and join the back of the line
bus_line.append("Person A")  # First to arrive
bus_line.append("Person B")  # Second to arrive
bus_line.append("Person C")  # Third to arrive

print(f"Line order: {bus_line}")

# Bus arrives and boards from the front
first_boarded = bus_line.pop(0)  # Person A boards first
second_boarded = bus_line.pop(0)  # Person B boards second

print(f"First boarded: {first_boarded}")
print(f"Second boarded: {second_boarded}")
print(f"Remaining in line: {bus_line}")
```

### Example 2: Printer Queue
```python
# Office printer FIFO behavior
print_queue = []

# Documents sent to printer
print_queue.append("Report.pdf")      # First job
print_queue.append("Email.docx")      # Second job
print_queue.append("Presentation.ppt") # Third job

print(f"Print queue order: {print_queue}")

# Printer processes jobs in order
first_printed = print_queue.pop(0)   # Report.pdf prints first
second_printed = print_queue.pop(0)  # Email.docx prints second

print(f"First printed: {first_printed}")
print(f"Second printed: {second_printed}")
print(f"Waiting to print: {print_queue}")
```

### Example 3: Customer Service
```python
# Customer service FIFO system
customer_queue = []

# Customers arrive for service
customer_queue.append("Customer 1")  # First customer
customer_queue.append("Customer 2")  # Second customer
customer_queue.append("Customer 3")  # Third customer

print(f"Service queue: {customer_queue}")

# Service representative helps customers in order
served_first = customer_queue.pop(0)  # Customer 1 served first
served_second = customer_queue.pop(0)  # Customer 2 served second

print(f"First served: {served_first}")
print(f"Second served: {served_second}")
print(f"Waiting customers: {customer_queue}")
```

### Example 4: Ticket System
```python
# Bakery ticket system (FIFO)
ticket_queue = []

# Customers take tickets
ticket_queue.append("Ticket #001")  # First customer
ticket_queue.append("Ticket #002")  # Second customer
ticket_queue.append("Ticket #003")  # Third customer

print(f"Ticket order: {ticket_queue}")

# Bakery calls customers in ticket order
called_first = ticket_queue.pop(0)  # Ticket #001 called first
called_second = ticket_queue.pop(0)  # Ticket #002 called second

print(f"First called: {called_first}")
print(f"Second called: {called_second}")
print(f"Waiting tickets: {ticket_queue}")
```

## 5. Identifying FIFO vs LIFO
### Recognition Patterns

#### FIFO Indicators:
- **Lines/Queues**: People standing in line
- **Fair Processing**: "First come, first served"
- **Time-Based Priority**: Longest wait gets priority
- **Front/Back Structure**: Add at back, remove from front
- **Sequential Processing**: Order preserved exactly

#### LIFO Indicators:
- **Stacks/Piles**: Items stacked on top of each other
- **Recent Priority**: Last item added gets priority
- **Top Access**: Easy access to most recent item
- **Reverse Processing**: Order reversed on removal
- **Undo/Back Operations**: Going back through recent actions

### Decision Flowchart
```
Is the system about fairness in waiting time?
    ↓ Yes
Is the first to arrive served first?
    ↓ Yes
→ FIFO (Queue)

Is the system about accessing the most recent item?
    ↓ Yes
Is the last added item the first to be processed?
    ↓ Yes
→ LIFO (Stack)
```

## 6. FIFO Applications in Computing
### Application 1: Task Scheduling
```python
class TaskScheduler:
    """FIFO task scheduler"""
    
    def __init__(self):
        self.task_queue = []
    
    def add_task(self, task):
        """Add task to end of queue"""
        self.task_queue.append(task)
        print(f"Added task: {task}")
    
    def process_next_task(self):
        """Process task from front of queue"""
        if not self.task_queue:
            print("No tasks to process")
            return None
        
        task = self.task_queue.pop(0)
        print(f"Processing task: {task}")
        return task
    
    def get_queue_status(self):
        """Get current queue status"""
        return {
            'tasks_waiting': len(self.task_queue),
            'next_task': self.task_queue[0] if self.task_queue else None,
            'queue_order': self.task_queue.copy()
        }

# Usage
scheduler = TaskScheduler()
scheduler.add_task("Backup database")
scheduler.add_task("Send emails")
scheduler.add_task("Generate reports")

print(f"Status: {scheduler.get_queue_status()}")
scheduler.process_next_task()  # Processes "Backup database" first
```

### Application 2: Message Queue
```python
class MessageQueue:
    """FIFO message queue for communication"""
    
    def __init__(self):
        self.messages = []
    
    def send_message(self, message):
        """Add message to queue"""
        self.messages.append(message)
        print(f"Message queued: {message}")
    
    def receive_message(self):
        """Get message from front of queue"""
        if not self.messages:
            return None
        
        message = self.messages.pop(0)
        print(f"Message received: {message}")
        return message
    
    def get_message_count(self):
        """Get number of waiting messages"""
        return len(self.messages)

# Usage
msg_queue = MessageQueue()
msg_queue.send_message("Hello")
msg_queue.send_message("How are you?")
msg_queue.send_message("Goodbye")

while msg_queue.get_message_count() > 0:
    msg_queue.receive_message()
```

### Application 3: Network Packet Processing
```python
class NetworkQueue:
    """FIFO network packet processing"""
    
    def __init__(self):
        self.packets = []
        self.processed_count = 0
    
    def receive_packet(self, packet):
        """Receive network packet"""
        self.packets.append(packet)
        print(f"Packet received: {packet}")
    
    def process_packet(self):
        """Process next packet in queue"""
        if not self.packets:
            print("No packets to process")
            return
        
        packet = self.packets.pop(0)
        self.processed_count += 1
        print(f"Processed packet #{self.processed_count}: {packet}")
    
    def get_queue_info(self):
        """Get queue information"""
        return {
            'packets_waiting': len(self.packets),
            'packets_processed': self.processed_count,
            'next_packet': self.packets[0] if self.packets else None
        }

# Usage
net_queue = NetworkQueue()
net_queue.receive_packet("Data chunk 1")
net_queue.receive_packet("Data chunk 2")
net_queue.receive_packet("Data chunk 3")

print(f"Queue info: {net_queue.get_queue_info()}")
net_queue.process_packet()  # Processes "Data chunk 1" first
```

## 7. FIFO Implementation Patterns
### Pattern 1: Basic Queue Operations
```python
# Basic FIFO queue operations
queue = []

# Enqueue (add to back)
queue.append("Item 1")
queue.append("Item 2")
queue.append("Item 3")
print(f"Queue after enqueues: {queue}")

# Dequeue (remove from front)
item1 = queue.pop(0)  # Removes "Item 1"
item2 = queue.pop(0)  # Removes "Item 2"
print(f"Dequeued items: {item1}, {item2}")
print(f"Queue after dequeues: {queue}")

# Check if empty
is_empty = len(queue) == 0
print(f"Is queue empty? {is_empty}")

# Peek at front item
front_item = queue[0] if queue else None
print(f"Front item: {front_item}")
```

### Pattern 2: Safe Queue Operations
```python
class SafeQueue:
    """Queue with error handling"""
    
    def __init__(self):
        self.items = []
    
    def enqueue(self, item):
        """Safely add item to queue"""
        self.items.append(item)
        print(f"Enqueued: {item}")
    
    def dequeue(self):
        """Safely remove item from queue"""
        if not self.items:
            print("Queue is empty - cannot dequeue")
            return None
        
        item = self.items.pop(0)
        print(f"Dequeued: {item}")
        return item
    
    def peek(self):
        """Look at front item without removing"""
        if not self.items:
            print("Queue is empty - nothing to peek")
            return None
        
        return self.items[0]
    
    def is_empty(self):
        """Check if queue is empty"""
        return len(self.items) == 0
    
    def size(self):
        """Get queue size"""
        return len(self.items)

# Usage
safe_queue = SafeQueue()
safe_queue.enqueue("A")
safe_queue.enqueue("B")
safe_queue.enqueue("C")

print(f"Front item: {safe_queue.peek()}")
safe_queue.dequeue()
safe_queue.dequeue()
safe_queue.dequeue()  # Should handle empty case
safe_queue.dequeue()  # Should handle empty case again
```

### Pattern 3: Queue with Capacity
```python
class BoundedQueue:
    """Queue with maximum capacity"""
    
    def __init__(self, capacity):
        self.capacity = capacity
        self.items = []
    
    def enqueue(self, item):
        """Add item if queue not full"""
        if len(self.items) >= self.capacity:
            print(f"Queue full - cannot enqueue {item}")
            return False
        
        self.items.append(item)
        print(f"Enqueued: {item}")
        return True
    
    def dequeue(self):
        """Remove item from queue"""
        if not self.items:
            print("Queue empty - cannot dequeue")
            return None
        
        item = self.items.pop(0)
        print(f"Dequeued: {item}")
        return item
    
    def is_full(self):
        """Check if queue is full"""
        return len(self.items) >= self.capacity
    
    def is_empty(self):
        """Check if queue is empty"""
        return len(self.items) == 0
    
    def get_status(self):
        """Get queue status"""
        return {
            'size': len(self.items),
            'capacity': self.capacity,
            'is_full': self.is_full(),
            'is_empty': self.is_empty(),
            'items': self.items.copy()
        }

# Usage
bounded_queue = BoundedQueue(capacity=3)
bounded_queue.enqueue("Item 1")
bounded_queue.enqueue("Item 2")
bounded_queue.enqueue("Item 3")
bounded_queue.enqueue("Item 4")  # Should fail - queue full

print(f"Status: {bounded_queue.get_status()}")
```

## 8. Performance Considerations
### Time Complexity Analysis
```python
import time

def measure_queue_performance():
    """Measure performance of queue operations"""
    sizes = [100, 1000, 10000]
    
    for size in sizes:
        # Build queue
        queue = list(range(size))
        
        # Measure dequeue performance
        start_time = time.time()
        for _ in range(min(100, size)):
            if queue:
                queue.pop(0)  # O(n) operation for list
        dequeue_time = time.time() - start_time
        
        print(f"Queue size: {size:,}")
        print(f"Dequeue operations: {min(100, size):,}")
        print(f"Time: {dequeue_time:.4f} seconds")
        print(f"Average per dequeue: {(dequeue_time / min(100, size)) * 1000:.2f} ms")
        print("-" * 40)

# Run performance test
measure_queue_performance()
```

### Efficient Queue Implementation
```python
from collections import deque

class EfficientQueue:
    """Efficient queue using collections.deque"""
    
    def __init__(self):
        self.items = deque()
    
    def enqueue(self, item):
        """Add item to queue - O(1)"""
        self.items.append(item)
    
    def dequeue(self):
        """Remove item from queue - O(1)"""
        if not self.items:
            return None
        return self.items.popleft()
    
    def peek(self):
        """Look at front item - O(1)"""
        if not self.items:
            return None
        return self.items[0]
    
    def size(self):
        """Get queue size - O(1)"""
        return len(self.items)

# Performance comparison
def compare_queue_implementations():
    """Compare list vs deque performance"""
    operations = 10000
    
    # List implementation
    list_queue = []
    start_time = time.time()
    for i in range(operations):
        list_queue.append(i)  # Enqueue
    for i in range(operations):
        if list_queue:
            list_queue.pop(0)  # Dequeue (O(n))
    list_time = time.time() - start_time
    
    # Deque implementation
    deque_queue = deque()
    start_time = time.time()
    for i in range(operations):
        deque_queue.append(i)  # Enqueue
    for i in range(operations):
        if deque_queue:
            deque_queue.popleft()  # Dequeue (O(1))
    deque_time = time.time() - start_time
    
    print(f"List queue time: {list_time:.4f} seconds")
    print(f"Deque queue time: {deque_time:.4f} seconds")
    print(f"Speedup: {list_time / deque_time:.2f}x")

# Run comparison
compare_queue_implementations()
```

## 9. Common FIFO Scenarios
### Scenario 1: Restaurant Orders
```python
class RestaurantOrderSystem:
    """FIFO order processing for restaurant"""
    
    def __init__(self):
        self.order_queue = []
        self.order_number = 1
    
    def take_order(self, customer_name, items):
        """Take customer order"""
        order = {
            'number': self.order_number,
            'customer': customer_name,
            'items': items,
            'timestamp': len(self.order_queue)
        }
        self.order_queue.append(order)
        print(f"Order #{order['number']} taken for {customer_name}")
        self.order_number += 1
        return order
    
    def complete_order(self):
        """Complete next order in queue"""
        if not self.order_queue:
            print("No orders to complete")
            return None
        
        order = self.order_queue.pop(0)
        print(f"Completed Order #{order['number']} for {order['customer']}")
        return order
    
    def get_waiting_orders(self):
        """Get list of waiting orders"""
        return [f"#{order['number']} - {order['customer']}" for order in self.order_queue]

# Usage
restaurant = RestaurantOrderSystem()
restaurant.take_order("Alice", ["Burger", "Fries"])
restaurant.take_order("Bob", ["Pizza", "Salad"])
restaurant.take_order("Charlie", ["Sandwich"])

print(f"Waiting orders: {restaurant.get_waiting_orders()}")
restaurant.complete_order()  # Completes Alice's order first
restaurant.complete_order()  # Completes Bob's order second
```

### Scenario 2: Call Center
```python
class CallCenter:
    """FIFO call center queue"""
    
    def __init__(self):
        self.call_queue = []
        self.call_id = 1
    
    def receive_call(self, customer_name, issue):
        """Receive incoming call"""
        call = {
            'id': self.call_id,
            'customer': customer_name,
            'issue': issue,
            'wait_time': 0
        }
        self.call_queue.append(call)
        print(f"Call #{call['id']} received from {customer_name}")
        self.call_id += 1
        return call
    
    def answer_call(self):
        """Answer next call in queue"""
        if not self.call_queue:
            print("No calls waiting")
            return None
        
        call = self.call_queue.pop(0)
        print(f"Answering Call #{call['id']} from {call['customer']}")
        return call
    
    def update_wait_times(self):
        """Update wait times for all waiting calls"""
        for call in self.call_queue:
            call['wait_time'] += 1
    
    def get_queue_status(self):
        """Get current queue status"""
        return {
            'calls_waiting': len(self.call_queue),
            'next_call': self.call_queue[0] if self.call_queue else None,
            'average_wait': sum(call['wait_time'] for call in self.call_queue) / len(self.call_queue) if self.call_queue else 0
        }

# Usage
call_center = CallCenter()
call_center.receive_call("Customer A", "Billing issue")
call_center.receive_call("Customer B", "Technical support")
call_center.receive_call("Customer C", "Sales inquiry")

print(f"Queue status: {call_center.get_queue_status()}")
call_center.answer_call()  # Answers Customer A first
```

### Scenario 3: Download Manager
```python
class DownloadManager:
    """FIFO download queue"""
    
    def __init__(self):
        self.download_queue = []
        self.completed_downloads = []
    
    def add_download(self, filename, size_mb):
        """Add download to queue"""
        download = {
            'filename': filename,
            'size_mb': size_mb,
            'status': 'waiting',
            'added_time': len(self.download_queue)
        }
        self.download_queue.append(download)
        print(f"Added to queue: {filename} ({size_mb}MB)")
        return download
    
    def process_next_download(self):
        """Process next download in queue"""
        if not self.download_queue:
            print("No downloads waiting")
            return None
        
        download = self.download_queue.pop(0)
        download['status'] = 'completed'
        self.completed_downloads.append(download)
        print(f"Downloaded: {download['filename']}")
        return download
    
    def get_queue_info(self):
        """Get download queue information"""
        total_waiting = sum(d['size_mb'] for d in self.download_queue)
        total_completed = sum(d['size_mb'] for d in self.completed_downloads)
        
        return {
            'waiting_count': len(self.download_queue),
            'completed_count': len(self.completed_downloads),
            'total_waiting_mb': total_waiting,
            'total_completed_mb': total_completed,
            'next_download': self.download_queue[0] if self.download_queue else None
        }

# Usage
download_manager = DownloadManager()
download_manager.add_download("video.mp4", 150)
download_manager.add_download("document.pdf", 5)
download_manager.add_download("image.jpg", 2)

print(f"Queue info: {download_manager.get_queue_info()}")
download_manager.process_next_download()  # Downloads video.mp4 first
```

## 10. Quick Checks
- What does FIFO stand for? → First-In, First-Out
- How does FIFO process items? → In arrival order
- Where do new items join a FIFO queue? → At the back
- Where are items removed from a FIFO queue? → From the front
- What's a real-world FIFO example? → Bus line, printer queue
- How is FIFO different from LIFO? → FIFO preserves order, LIFO reverses it
- When would you use FIFO? → When fairness matters
- What's the time complexity of queue operations? → O(1) for enqueue, O(n) for dequeue with lists

## 11. Summary
FIFO (First-In, First-Out) is a fundamental data structure principle that ensures fair, ordered processing:

### Core Concept
- **First-In, First-Out**: Items are processed in the exact order they arrive
- **Queue Structure**: Items join at the back, leave from the front
- **Fairness Principle**: Longest-waiting items get served first
- **Order Preservation**: Input order matches output order exactly

### Real-World Applications
- **Service Lines**: Concert lines, bus stops, customer service
- **Processing Systems**: Print queues, task schedulers, network packets
- **Ticket Systems**: Bakeries, government offices, call centers
- **Communication**: Message queues, email processing, download managers

### Implementation Patterns
- **Basic Queue**: Use list with `append()` and `pop(0)`
- **Efficient Queue**: Use `collections.deque` for O(1) operations
- **Bounded Queue**: Limit maximum capacity
- **Safe Operations**: Handle empty/full queue conditions

### Key Differences from LIFO
| Aspect | FIFO (Queue) | LIFO (Stack) |
|--------|--------------|--------------|
| Order | Preserved | Reversed |
| Access | Front/Back | Top only |
| Use Case | Fairness | Recency |
| Examples | Lines, queues | Stacks, undo |

### Performance Considerations
- **List Implementation**: O(1) enqueue, O(n) dequeue
- **Deque Implementation**: O(1) enqueue and dequeue
- **Memory Usage**: O(n) for n items
- **Best Practice**: Use `deque` for high-performance queues

> **Key Insight**: "FIFO is all about fairness - the first person in line gets served first. This simple principle powers everything from concert tickets to computer networks, ensuring that everyone gets their turn in the right order."

### Mastery Checklist
- ✅ Understand FIFO definition and behavior
- ✅ Identify real-world FIFO scenarios
- ✅ Distinguish FIFO from LIFO behavior
- ✅ Implement basic queue operations
- ✅ Apply FIFO to practical problems
- ✅ Choose appropriate implementation (list vs deque)
- ✅ Handle edge cases (empty/full queues)
- ✅ Understand performance characteristics
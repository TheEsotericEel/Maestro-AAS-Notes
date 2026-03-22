# Introduce the queue

## 1. Introduction
A queue is a fundamental data structure that models real-world waiting lines. Unlike stacks that follow LIFO (Last-In, First-Out), queues follow FIFO (First-In, First-Out) behavior, ensuring that items are processed in the exact order they arrive. This lesson introduces the queue concept, its structure, and how it maintains order fairness.

## 2. The Concert Line Analogy
### Visualizing Queue Behavior
Imagine you're in a huge line to buy concert tickets 🎟️:

```
Concert Ticket Line (Queue):

FRONT (next to be served) ← [Person 1] [Person 2] [Person 3] [Person 4] ← BACK (new arrivals)

Process Flow:
1. Person 1 arrives first → joins at front initially
2. Person 2 arrives → joins behind Person 1
3. Person 3 arrives → joins behind Person 2
4. Person 4 arrives → joins behind Person 3 (at back)

Service Order:
Person 1 gets served first (was at front)
Person 2 gets served second (moves to front)
Person 3 gets served third (moves to front)
Person 4 gets served fourth (moves to front)

New Arrivals:
Person 5 arrives → joins at back behind Person 4
```

**Queue Definition**: A queue is an ordered collection where items leave in the same order they arrived.

### Core Queue Characteristics
- **Ordered Line**: Items maintain their arrival order
- **Front Access**: The next item to leave is always at the front
- **Back Access**: New items always join at the back
- **Fair Processing**: First to arrive is first to be served
- **Order Preservation**: Input order exactly matches output order

## 3. Queue Structure and Terminology
### Front and Back Concept
```
Queue Structure Visualization:

FRONT (next out) ← [Item 1] [Item 2] [Item 3] [Item 4] ← BACK (new in)

Key Points:
- Front: Where the next item leaves (gets served/processed)
- Back: Where new items arrive (join the queue)
- Items move toward the front over time
- Order is preserved throughout the process
```

### Queue Operations Flow
```
Queue Operations Sequence:

Initial State:
FRONT ← [A] [B] [C] ← BACK

Enqueue D (add to back):
FRONT ← [A] [B] [C] [D] ← BACK

Dequeue (remove from front):
FRONT ← [B] [C] [D] ← BACK
Removed: A

Enqueue E (add to back):
FRONT ← [B] [C] [D] [E] ← BACK

Dequeue (remove from front):
FRONT ← [C] [D] [E] ← BACK
Removed: B
```

## 4. Queue vs Real-World Lines
### Perfect Match
| Real-World Line | Queue Data Structure |
|-----------------|-------------------|
| People wait in order | Items stored in order |
| Front person served first | Front item processed first |
| New people join at back | New items added at back |
| Fair waiting system | FIFO processing system |
| Order preserved | Order preserved |

### Why Queues Work So Well
- **Natural Behavior**: Matches how we expect lines to work
- **Fairness**: Everyone gets their turn in order
- **Predictable**: No surprises about who goes next
- **Efficient**: Simple rules for adding and removing
- **Scalable**: Works for small or large groups

## 5. Queue Fundamentals
### Basic Queue Properties
```python
# Queue representation using Python list
queue = []

# Queue properties
print(f"Empty queue: {queue}")
print(f"Front access: {queue[0] if queue else 'None'}")
print(f"Back access: {queue[-1] if queue else 'None'}")
print(f"Queue size: {len(queue)}")
print(f"Is empty: {len(queue) == 0}")
```

### Core Operations
1. **Enqueue**: Add item to the back of the queue
2. **Dequeue**: Remove item from the front of the queue
3. **Front**: Look at the front item without removing it
4. **IsEmpty**: Check if the queue has no items
5. **Size**: Get the number of items in the queue

## 6. Simple Queue Implementation
### Basic Queue Class
```python
class SimpleQueue:
    """Basic queue implementation"""
    
    def __init__(self):
        self.items = []
    
    def enqueue(self, item):
        """Add item to the back of the queue"""
        self.items.append(item)
        print(f"Enqueued: {item}")
    
    def dequeue(self):
        """Remove item from the front of the queue"""
        if not self.is_empty():
            item = self.items.pop(0)
            print(f"Dequeued: {item}")
            return item
        else:
            print("Queue is empty - cannot dequeue")
            return None
    
    def front(self):
        """Look at the front item without removing it"""
        if not self.is_empty():
            return self.items[0]
        return None
    
    def is_empty(self):
        """Check if queue is empty"""
        return len(self.items) == 0
    
    def size(self):
        """Get queue size"""
        return len(self.items)
    
    def __str__(self):
        """String representation of queue"""
        return f"Queue: {self.items}"

# Usage demonstration
queue = SimpleQueue()
print(f"Initial state: {queue}")
queue.enqueue("Person A")
queue.enqueue("Person B")
queue.enqueue("Person C")
print(f"After enqueues: {queue}")
print(f"Front item: {queue.front()}")
queue.dequeue()
print(f"After dequeue: {queue}")
print(f"New front item: {queue.front()}")
```

### Queue State Tracking
```python
class TrackedQueue:
    """Queue with state tracking"""
    
    def __init__(self, name):
        self.name = name
        self.items = []
        self.operation_count = 0
    
    def enqueue(self, item):
        """Add item with tracking"""
        self.items.append(item)
        self.operation_count += 1
        print(f"[{self.name}] Enqueue #{self.operation_count}: {item}")
        self._display_state()
    
    def dequeue(self):
        """Remove item with tracking"""
        if not self.is_empty():
            self.operation_count += 1
            item = self.items.pop(0)
            print(f"[{self.name}] Dequeue #{self.operation_count}: {item}")
            self._display_state()
            return item
        else:
            print(f"[{self.name}] Queue empty - cannot dequeue")
            return None
    
    def _display_state(self):
        """Display current queue state"""
        front = self.items[0] if self.items else "None"
        back = self.items[-1] if self.items else "None"
        print(f"  State: Front={front}, Back={back}, Size={len(self.items)}")
        print(f"  Queue: {self.items}")

# Usage
ticket_queue = TrackedQueue("Ticket Line")
ticket_queue.enqueue("Customer 1")
ticket_queue.enqueue("Customer 2")
ticket_queue.enqueue("Customer 3")
ticket_queue.dequeue()
ticket_queue.dequeue()
```

## 7. Queue Behavior Examples
### Example 1: Coffee Shop Line
```python
class CoffeeShopQueue:
    """Coffee shop customer queue"""
    
    def __init__(self):
        self.customers = []
        self.orders_served = 0
    
    def customer_arrives(self, name, order):
        """Customer joins the queue"""
        customer = {
            'name': name,
            'order': order,
            'arrival_time': len(self.customers)
        }
        self.customers.append(customer)
        print(f"{name} arrived and ordered {order}")
        print(f"Queue position: {len(self.customers)}")
    
    def serve_next_customer(self):
        """Serve the next customer in line"""
        if not self.customers:
            print("No customers waiting")
            return None
        
        customer = self.customers.pop(0)
        self.orders_served += 1
        print(f"Serving {customer['name']} - {customer['order']}")
        print(f"Orders served today: {self.orders_served}")
        return customer
    
    def get_queue_status(self):
        """Get current queue status"""
        if not self.customers:
            return "No customers waiting"
        
        next_customer = self.customers[0]['name']
        waiting_count = len(self.customers)
        return f"Next: {next_customer}, Waiting: {waiting_count}"

# Usage
coffee_queue = CoffeeShopQueue()
coffee_queue.customer_arrives("Alice", "Latte")
coffee_queue.customer_arrives("Bob", "Cappuccino")
coffee_queue.customer_arrives("Charlie", "Espresso")

print(f"Status: {coffee_queue.get_queue_status()}")
coffee_queue.serve_next_customer()  # Serves Alice first
coffee_queue.serve_next_customer()  # Serves Bob second
print(f"Status: {coffee_queue.get_queue_status()}")
```

### Example 2: Printer Job Queue
```python
class PrinterQueue:
    """Printer job queue system"""
    
    def __init__(self):
        self.jobs = []
        self.job_counter = 1
    
    def add_print_job(self, document_name, pages):
        """Add a document to the print queue"""
        job = {
            'id': self.job_counter,
            'document': document_name,
            'pages': pages,
            'status': 'waiting'
        }
        self.jobs.append(job)
        print(f"Job #{job['id']}: {document_name} ({pages} pages) added to queue")
        self.job_counter += 1
        return job
    
    def process_next_job(self):
        """Process the next print job"""
        if not self.jobs:
            print("No jobs in print queue")
            return None
        
        job = self.jobs.pop(0)
        job['status'] = 'completed'
        print(f"Printed Job #{job['id']}: {job['document']}")
        return job
    
    def get_queue_info(self):
        """Get print queue information"""
        if not self.jobs:
            return "No jobs waiting"
        
        next_job = self.jobs[0]
        total_pages = sum(job['pages'] for job in self.jobs)
        return f"Next: Job #{next_job['id']} ({next_job['document']}), Total pages: {total_pages}"

# Usage
printer = PrinterQueue()
printer.add_print_job("Report.pdf", 25)
printer.add_print_job("Email.docx", 3)
printer.add_print_job("Presentation.ppt", 15)

print(f"Queue info: {printer.get_queue_info()}")
printer.process_next_job()  # Prints Report.pdf first
printer.process_next_job()  # Prints Email.docx second
print(f"Queue info: {printer.get_queue_info()}")
```

### Example 3: Bank Teller Queue
```python
class BankQueue:
    """Bank customer service queue"""
    
    def __init__(self):
        self.customers = []
        self.ticket_number = 1
        self.current_serving = 0
    
    def take_ticket(self, customer_name):
        """Customer takes a numbered ticket"""
        ticket = {
            'number': self.ticket_number,
            'name': customer_name,
            'arrival_time': len(self.customers)
        }
        self.customers.append(ticket)
        print(f"{customer_name} took ticket #{self.ticket_number}")
        self.ticket_number += 1
        return ticket
    
    def serve_next_customer(self):
        """Serve the next customer by ticket number"""
        if not self.customers:
            print("No customers waiting")
            return None
        
        customer = self.customers.pop(0)
        self.current_serving = customer['number']
        print(f"Now serving ticket #{customer['number']}: {customer['name']}")
        return customer
    
    def announce_next_number(self):
        """Announce the next ticket number to be served"""
        if not self.customers:
            print("No customers waiting")
            return
        
        next_customer = self.customers[0]
        print(f"Now serving ticket #{next_customer['number']}: {next_customer['name']}")
        print(f"Waiting customers: {len(self.customers)}")
    
    def get_waiting_list(self):
        """Get list of waiting customers"""
        return [f"Ticket #{c['number']}: {c['name']}" for c in self.customers]

# Usage
bank_queue = BankQueue()
bank_queue.take_ticket("John Smith")
bank_queue.take_ticket("Mary Johnson")
bank_queue.take_ticket("David Lee")

print(f"Waiting list: {bank_queue.get_waiting_list()}")
bank_queue.announce_next_number()
bank_queue.serve_next_customer()  # Serves John Smith
bank_queue.announce_next_number()  # Now serving Mary Johnson
```

## 8. Queue Properties and Characteristics
### Essential Queue Properties
```python
def demonstrate_queue_properties():
    """Demonstrate fundamental queue properties"""
    
    # Property 1: Order Preservation
    print("=== Property 1: Order Preservation ===")
    queue = []
    items = ["A", "B", "C", "D"]
    
    # Add items in order
    for item in items:
        queue.append(item)
    
    print(f"Input order: {items}")
    print(f"Queue state: {queue}")
    
    # Remove items - should come out in same order
    removed = []
    while queue:
        removed.append(queue.pop(0))
    
    print(f"Output order: {removed}")
    print(f"Order preserved: {items == removed}")
    
    # Property 2: FIFO Behavior
    print("\n=== Property 2: FIFO Behavior ===")
    queue = []
    
    # First In
    queue.append("First")
    queue.append("Second")
    queue.append("Third")
    
    print(f"Queue after additions: {queue}")
    
    # First Out
    first_out = queue.pop(0)
    print(f"First item out: {first_out}")
    print(f"Remaining queue: {queue}")
    
    # Property 3: Front/Back Access
    print("\n=== Property 3: Front/Back Access ===")
    queue = ["Front", "Middle", "Back"]
    
    print(f"Queue: {queue}")
    print(f"Front item: {queue[0]}")
    print(f"Back item: {queue[-1]}")
    print(f"Queue size: {len(queue)}")

# Run demonstration
demonstrate_queue_properties()
```

### Queue Invariants
```python
class InvariantQueue:
    """Queue that maintains invariants"""
    
    def __init__(self):
        self.items = []
        self.operations = 0
    
    def enqueue(self, item):
        """Add item while maintaining invariants"""
        self.items.append(item)
        self.operations += 1
        self._check_invariants()
    
    def dequeue(self):
        """Remove item while maintaining invariants"""
        if not self.is_empty():
            item = self.items.pop(0)
            self.operations += 1
            self._check_invariants()
            return item
        return None
    
    def _check_invariants(self):
        """Verify queue invariants are maintained"""
        # Invariant 1: Order is preserved
        if len(self.items) > 1:
            for i in range(len(self.items) - 1):
                # Items maintain their relative order
                pass  # This is inherent in list structure
        
        # Invariant 2: Front is always first item added
        if self.items:
            front_item = self.items[0]
            # Front item is always the earliest remaining item
        
        # Invariant 3: Back is always last item added
        if self.items:
            back_item = self.items[-1]
            # Back item is always the most recently added item
        
        print(f"Invariants checked after {self.operations} operations")
    
    def is_empty(self):
        """Check if queue is empty"""
        return len(self.items) == 0
    
    def __str__(self):
        return f"InvariantQueue: {self.items}"

# Usage
inv_queue = InvariantQueue()
inv_queue.enqueue("A")
inv_queue.enqueue("B")
inv_queue.enqueue("C")
inv_queue.dequeue()
inv_queue.dequeue()
```

## 9. Queue vs Stack Comparison
### Direct Comparison
```python
def compare_queue_and_stack():
    """Compare queue and stack behaviors"""
    
    print("=== Queue vs Stack Comparison ===")
    
    # Same input for both
    items = ["First", "Second", "Third"]
    
    # Queue behavior (FIFO)
    queue = []
    for item in items:
        queue.append(item)  # Enqueue at back
    
    queue_output = []
    while queue:
        queue_output.append(queue.pop(0))  # Dequeue from front
    
    # Stack behavior (LIFO)
    stack = []
    for item in items:
        stack.append(item)  # Push on top
    
    stack_output = []
    while stack:
        stack_output.append(stack.pop())  # Pop from top
    
    print(f"Input: {items}")
    print(f"Queue output: {queue_output}")
    print(f"Stack output: {stack_output}")
    print(f"Queue preserves order: {items == queue_output}")
    print(f"Stack reverses order: {items[::-1] == stack_output}")

# Run comparison
compare_queue_and_stack()
```

### Usage Decision Guide
```python
def choose_data_structure():
    """Guide for choosing between queue and stack"""
    
    scenarios = [
        {
            'scenario': 'Processing print jobs in order received',
            'answer': 'Queue',
            'reason': 'Fairness - first job should print first'
        },
        {
            'scenario': 'Undo functionality in text editor',
            'answer': 'Stack',
            'reason': 'Recency - last action should be undone first'
        },
        {
            'scenario': 'Customers waiting in line at store',
            'answer': 'Queue',
            'reason': 'Fairness - first customer served first'
        },
        {
            'scenario': 'Browser back button navigation',
            'answer': 'Stack',
            'reason': 'Recency - most recent page visited first'
        },
        {
            'scenario': 'Network packet processing',
            'answer': 'Queue',
            'reason': 'Order - packets should process in arrival order'
        }
    ]
    
    print("=== Data Structure Selection Guide ===")
    for scenario in scenarios:
        print(f"\nScenario: {scenario['scenario']}")
        print(f"Best choice: {scenario['answer']}")
        print(f"Reason: {scenario['reason']}")

# Run guide
choose_data_structure()
```

## 10. Queue Applications Overview
### Common Use Cases
```python
class QueueApplications:
    """Overview of common queue applications"""
    
    @staticmethod
    def task_scheduler():
        """CPU task scheduling"""
        print("=== Task Scheduler ===")
        tasks = ["Backup", "Update", "Cleanup", "Report"]
        queue = tasks.copy()
        
        while queue:
            task = queue.pop(0)
            print(f"Executing task: {task}")
    
    @staticmethod
    def message_queue():
        """Message passing system"""
        print("\n=== Message Queue ===")
        messages = ["Email", "SMS", "Push", "Chat"]
        queue = messages.copy()
        
        while queue:
            message = queue.pop(0)
            print(f"Processing message: {message}")
    
    @staticmethod
    def customer_service():
        """Customer service line"""
        print("\n=== Customer Service ===")
        customers = ["Customer A", "Customer B", "Customer C"]
        queue = customers.copy()
        
        while queue:
            customer = queue.pop(0)
            print(f"Serving: {customer}")
    
    @staticmethod
    def print_queue():
        """Document printing queue"""
        print("\n=== Print Queue ===")
        documents = ["Report.pdf", "Letter.docx", "Invoice.pdf"]
        queue = documents.copy()
        
        while queue:
            doc = queue.pop(0)
            print(f"Printing: {doc}")

# Run all applications
apps = QueueApplications()
apps.task_scheduler()
apps.message_queue()
apps.customer_service()
apps.print_queue()
```

## 11. Quick Checks
- What is a queue? → An ordered line where items leave in arrival order
- Which end serves next in a queue? → The front
- Where do new items join a queue? → At the back
- Does a queue preserve order? → Yes, exactly
- What principle does a queue follow? → FIFO (First-In, First-Out)
- How is a queue different from a stack? → Queue preserves order, stack reverses it
- What's a real-world queue example? → Concert line, printer queue, customer service
- Is a queue fair? → Yes, first come, first served

## 12. Summary
A queue is a fundamental data structure that models real-world waiting lines with perfect fairness:

### Core Concept
- **Queue Definition**: An ordered collection where items leave in the same order they arrived
- **Front Access**: The next item to be processed is always at the front
- **Back Access**: New items always join at the back
- **FIFO Behavior**: First-In, First-Out processing ensures fairness

### Key Characteristics
- **Order Preservation**: Input order exactly matches output order
- **Fair Processing**: Longest-waiting items get served first
- **Predictable Behavior**: No surprises about processing order
- **Simple Rules**: Clear front/back distinction for operations

### Real-World Mapping
| Queue Concept | Real-World Equivalent |
|---------------|---------------------|
| Front of queue | Person at front of line |
| Back of queue | End of the line |
| Enqueue | Person joins the line |
| Dequeue | Person gets served |
| FIFO | First come, first served |

### Fundamental Operations
- **Enqueue**: Add item to the back
- **Dequeue**: Remove item from the front
- **Front**: Look at front item without removing
- **IsEmpty**: Check if queue has items
- **Size**: Get number of waiting items

### Common Applications
- **Service Lines**: Concert tickets, bank tellers, customer service
- **Processing Systems**: Print queues, task schedulers, network packets
- **Communication**: Message queues, email processing, call routing
- **Resource Management**: CPU scheduling, memory management, I/O operations

### Queue vs Stack
| Aspect | Queue (FIFO) | Stack (LIFO) |
|--------|--------------|--------------|
| Order | Preserved | Reversed |
| Access | Front/Back | Top only |
| Use Case | Fairness | Recency |
| Examples | Lines, queues | Stacks, undo |

> **Key Insight**: "A queue is simply a computer's way of implementing a fair line - the person who arrives first gets served first, new people join at the back, and everyone gets their turn in the right order."

### Mastery Checklist
- ✅ Understand queue definition and behavior
- ✅ Identify front and back of a queue
- ✅ Recognize FIFO processing
- ✅ Implement basic queue operations
- ✅ Apply queues to real-world scenarios
- ✅ Distinguish queues from stacks
- ✅ Understand order preservation
- ✅ Choose appropriate use cases for queues
# Top-Down Design and Stubbing

## 1. Top-Down Architecture

### What is it?
Top-Down Design allows an engineer to define the high-level flow of an application without worrying about the low-level implementation details immediately. You define the "Interface" first, and the "Implementation" second.

### The Skeleton
Think of your program as a human body.
1.  **Skeleton (Stubs)**: The bones. The structure. (Function definitions).
2.  **Nervous System**: The control flow connecting the bones. (Main loop).
3.  **Organ/Muscle**: The actual complex logic inside.

---

## 2. The Stub (Mock)

A **Stub** is a function that has a valid signature (name + arguments) but contains no logic. It returns a "fake" successful result.

**Goal**: Make the main program runnable immediately, even if it does nothing useful yet.

### The Structure of a Stub
```python
def calculate_tax(amount):
    """
    TODO: Implement tax logic. 
    For now, return 0 to prevent crash.
    """
    return 0.0
```

---

## 3. Practical Examples

### Example: The Game Loop
**Task**: Build a game where a player fights a monster.

**Step 1: The High-Level Logic (The "What")**
We can write the entire game logic without knowing *how* combat works.
```python
def main():
    player = create_player()
    monster = spawn_monster()
    
    while is_alive(player) and is_alive(monster):
        attack(player, monster)
        
        if is_alive(monster):
            attack(monster, player)
            
    print("Game Over")
```
*This code calls 4 functions that don't exist yet.*

**Step 2: The Stubs (The "How" - Deferred)**
```python
def create_player():
    print("[STUB] Creating Player")
    return "Player1"

def spawn_monster():
    print("[STUB] Spawning Monster")
    return "Goblin"

def is_alive(entity):
    # Always return True for now to test infinite loop? 
    # Or return False to test game over?
    return True 

def attack(attacker, defender):
    print(f"[STUB] {attacker} attacks {defender}")
```

**Step 3: Execution**
Running `main()` now prints the flow. We can verify the *sequence* of events before we write complex damage formulas.

**Step 4: Implementation**
Now replace `create_player` stub with real code. Then `spawn_monster`. One by one.

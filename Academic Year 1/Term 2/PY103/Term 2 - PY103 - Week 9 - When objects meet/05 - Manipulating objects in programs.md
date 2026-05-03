# Manipulating Objects in Programs

## 1. Lesson Focus
Using loops to modify object state (attributes) and then using the updated object data to calculate program-level results like counts and summaries.

## 2. Core Concepts
**State Modification in Loop**: Looping over objects and calling methods that change their attributes (e.g., `pet.feed()`, `player.upgrade()`).

**List Stays Same, Objects Change**: The list structure remains unchanged—only the attributes of the objects inside the list are modified.

**Two-Step Pattern**: First loop to modify object state, then second loop (or separate logic) to calculate summaries using the updated data.

**Summary After Loop**: Print summary results outside the loop to get a single clean output instead of repeated prints.

## 3. Key Details to Remember
- Loop calls methods that modify object attributes
- List length and object references stay the same
- Attribute changes happen inside the methods (e.g., `self.hunger -= 3`)
- Print summaries after loops complete, not inside them
- Use object data after modification for program-level results

## 4. Implementation Pattern

**Modify Then Count Pattern**:
```python
# Step 1: Modify object state
for object in objects:
    object.modify()

# Step 2: Calculate summary using updated data
count = 0
for object in objects:
    if object.condition():
        count += 1

print("Summary:", count)  # Outside loop
```

## 5. Examples

### Example 1: Feeding Pets
```python
class Pet:
    """Represents a pet with hunger and happiness."""

    def __init__(self, name, hunger, happiness):
        self.name = name
        self.hunger = hunger
        self.happiness = happiness

    def feed(self):
        """Reduce hunger and increase happiness."""
        self.hunger -= 3
        self.happiness += 2

    def is_full(self):
        """Return True if this pet is not hungry anymore."""
        return self.hunger <= 2


# ---- Main program ----

pets = [
    Pet("Fido", hunger=8, happiness=3),
    Pet("Luna", hunger=6, happiness=4),
    Pet("Milo", hunger=5, happiness=5)
]

# 1) Change each pet
for pet in pets:
    pet.feed()

# 2) Use their data to build a summary
full_count = 0
for pet in pets:
    if pet.is_full():
        full_count += 1

print("Number of full pets:", full_count)
```

### Example 2: Upgrading Players
```python
class Player:
    """Represents a game player with a score."""

    def __init__(self, name, score):
        self.name = name
        self.score = score

    def upgrade(self):
        self.score += 20


# --- Main program ---

players = [
    Player("Alex", 85),
    Player("Jordan", 95),
    Player("Sam", 70)
]

# First loop: modify state
for player in players:
    player.upgrade()

# Second loop: count based on updated state
bonus_count = 0
for player in players:
    if player.score >= 100:
        bonus_count += 1

print("Number of players with bonus score:", bonus_count)
```

### Example 3: Turning On Lamps
```python
class Lamp:
    def __init__(self, is_on=False):
        self.is_on = is_on

    def turn_on(self):
        self.is_on = True

lamps = [Lamp() for _ in range(5)]

for lamp in lamps:
    lamp.turn_on()
# is_on attribute changes for each lamp
# lamps list structure unchanged
```

## 6. Common Mistakes / What Not to Do
- **Printing inside loop**: Printing counts inside the loop prints once per item instead of a single summary. Move prints outside the loop.
- **Confusing list change with object change**: The list doesn't change—only the attributes of objects inside it change.
- **Forgetting two-step pattern**: Trying to count before modifying state gives incorrect results. Modify first, then count.
- **Modifying wrong thing**: Ensure methods modify `self.attribute`, not create new objects or change the list structure.

## 7. Open-Note Review
- Loop calls methods that modify object attributes
- List structure stays the same, object state changes
- Attribute changes happen inside methods via `self.attribute = value`
- Two-step pattern: modify state, then calculate summary
- Print summaries outside loops for clean output
- Use updated object data for program-level results

## 8. Final Takeaway
Modify object state in loops by calling methods that change attributes, then use the updated object data to calculate program-level summaries—print results after the loop completes for clean output.

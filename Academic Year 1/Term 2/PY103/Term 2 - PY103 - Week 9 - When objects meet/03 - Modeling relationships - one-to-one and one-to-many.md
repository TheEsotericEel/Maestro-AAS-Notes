# Modeling Relationships: One-to-One and One-to-Many

## 1. Lesson Focus
Understanding how to model relationships between objects—specifically one-to-many relationships where one object is connected to many related objects.

## 2. Core Concepts
**One-to-Many Relationship**: A relationship where one object is associated with multiple related objects (e.g., one PetOwner → many Pets).

**Relationship Owner**: The object that stores the relationship, typically the "one" side when the main question is "which things belong to this one?"

**List Attribute**: Using a list to store references to multiple related objects (e.g., `self.pets = []`).

**One-to-One Link**: A reverse relationship where each related object references back to its owner (e.g., `self.owner` on a Pet).

## 3. Key Details to Remember
- Store the relationship on the "one" side using a list attribute
- Use a method to add objects to the relationship (e.g., `add_pet()`)
- The relationship is just pointers to objects, not copies
- Changing a related object's state doesn't break the relationship
- Design choice: where to store the relationship depends on your main use case

## 4. Implementation Pattern

**One-to-Many Pattern**:
```python
class PetOwner:
    def __init__(self, name):
        self.name = name
        self.pets = []  # list to hold many Pet objects

    def add_pet(self, pet):
        self.pets.append(pet)
```

**One-to-One Reverse Link** (optional):
```python
class Pet:
    def __init__(self, name, owner):
        self.name = name
        self.owner = owner  # reference back to owner
```

## 5. Examples

### Example 1: PetOwner with Many Pets
```python
class Pet:
    def __init__(self, name):
        self.name = name

class PetOwner:
    def __init__(self, name):
        self.name = name
        self.pets = []

    def add_pet(self, pet):
        self.pets.append(pet)

maria = PetOwner("Maria")
luna = Pet("Luna")
doug = Pet("Doug")
bob = Pet("Bob")

maria.add_pet(luna)
maria.add_pet(doug)
maria.add_pet(bob)

print(len(maria.pets))  # Output: 3
```

### Example 2: State Changes Don't Break Relationships
```python
luna.name = "Luna the Great"
# maria.pets still points to the same Pet object
# The list doesn't need to change
```

## 6. Design Guidelines
**Store Relationship on "One" Side When**:
- Main question is "which things belong to this one?"
- Example: "What pets does this owner have?"

**Add Reverse Link When**:
- Need to navigate from related object back to owner
- Example: "Who owns this pet?"

**Other One-to-Many Examples**:
- Library → many Books
- Teacher → many Students
- Team → many Players

## 7. Common Mistakes / What Not to Do
- **Storing relationship on "many" side**: If main use case is "what belongs to this one?", store on the one side, not each related object.
- **Confusing relationship with data**: The relationship is just pointers; changing a pet's name doesn't require updating the owner's list.
- **Forgetting add methods**: Provide methods to manage the relationship cleanly rather than direct list manipulation.

## 8. Open-Note Review
- One-to-many: one object holds list of many related objects
- Store relationship on "one" side for "what belongs to this?" queries
- Use list attribute (e.g., `self.pets = []`)
- Add method to manage relationship (e.g., `add_pet()`)
- State changes on related objects don't break relationship
- Optional: add reverse link for bidirectional navigation

## 9. Final Takeaway
Model one-to-many relationships by storing a list of related objects on the "one" side—the relationship is just pointers, so changing a related object's state doesn't break the connection.

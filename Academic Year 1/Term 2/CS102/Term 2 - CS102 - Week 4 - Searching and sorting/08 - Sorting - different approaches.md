# Sorting: Different Approaches

## 1. Lesson Focus
Understanding three high-level sorting strategies and how to recognize them from descriptions and real-world scenarios.

## 2. Core Concepts
**Sorting Strategy**: A method or algorithm for arranging items in a consistent order.

**Three Main Approaches**:
- Swap neighbours until no pair is out of order
- Keep picking the smallest from remaining items and place it next
- Maintain a sorted part and insert each new item into the correct position

## 3. Strategy Descriptions

**Approach 1: Swap Neighbours**
- Scan left to right through the collection
- Compare each pair of adjacent items
- Swap if they're in the wrong order
- Repeat passes until a full pass has no swaps
- Pattern: "Look at neighbours → if wrong, swap → keep walking until no swaps"

**Approach 2: Selection (Pick Smallest)**
- Look at all remaining items
- Find the smallest item
- Place it at the front of the sorted section
- Repeat with remaining items
- Pattern: "From what's left, pick the smallest and place it next in line"

**Approach 3: Insertion (Sorted Part)**
- Maintain a sorted portion
- Take the next unsorted item
- Insert it into the correct position within the sorted portion
- Repeat until all items are in the sorted portion
- Pattern: "Maintain a sorted part, and insert each new item into the right place inside it"

## 4. Examples

### Example 1: Books on Floor (Selection)
- Look over all books on the floor
- Grab the book with earliest alphabetical title
- Put it on empty shelf as first book
- From remaining floor books, find earliest and place next
- Repeat until all books are on shelf in order
- **Strategy**: Pick the smallest and place it next

### Example 2: Numbered Tiles (Swap Neighbours)
- Start at left, look at first two tiles
- If wrong order (bigger on left), swap them
- Move right, compare next pair, swap if needed
- Keep walking right, fixing neighbour pairs
- Go back to left, do another pass
- Repeat until full walk has no swaps
- **Strategy**: Swap neighbours until nothing is out of order

### Example 3: Cards in Hand (Insertion)
- Take first card, put in hand (sorted)
- Pick up next card, slide into correct spot in hand
- Pick up next card, insert into right position
- Repeat until no cards left on table
- **Strategy**: Keep a sorted part and insert each new item into it

## 5. Recognition Patterns
**Swap Neighbours Keywords**: "neighbours", "adjacent", "pair", "swap", "pass", "walk through"

**Selection Keywords**: "smallest", "minimum", "find", "place next", "from remaining", "pick"

**Insertion Keywords**: "insert", "slide into", "sorted part", "maintain sorted", "hand", "correct spot"

## 6. Common Mistakes / What Not to Do
- **Confusing selection with insertion**: Selection picks from all remaining, insertion maintains sorted portion and places into it.
- **Forgetting the "sorted part" concept**: Insertion always has a growing sorted section, selection builds sorted from front.
- **Mixing up swap patterns**: Swap neighbours always compares adjacent items, not arbitrary pairs.

## 7. Open-Note Review
- Swap neighbours: compare adjacent, swap if wrong, repeat until no swaps
- Selection: pick smallest from remaining, place next
- Insertion: maintain sorted part, insert each new item into correct position
- All three achieve sorted result, just different strategies

## 8. Final Takeaway
Different sorting strategies use different mental models—swap neighbours fixes adjacent pairs, selection repeatedly picks the smallest, and insertion grows a sorted portion by placing each item correctly.

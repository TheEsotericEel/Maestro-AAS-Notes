# Objects = Data + Behavior

## 1. Lesson Focus
Builds the core mental model for OOP: every object bundles **state** (data/facts about it) and **behavior** (actions it can do) into a single unit.

---

## 2. Core Concepts

### Object
An object is one "thing" that holds two parts together:

| Part | Also called | What it means |
|------|------------|---------------|
| **State** | Data / attributes | Facts about the object right now |
| **Behavior** | Actions / methods | Things the object can do |

> **Object = State + Behavior**

### State vs. Behavior — How to Tell Them Apart
- **State** → a fact, condition, or measurement: *"Battery level is 25%"*, *"Balance is $500"*, *"Age is 3"*
- **Behavior** → an action or process the object performs: *"The phone vibrates"*, *"Withdraw $50"*, *"Buddy barks"*

A quick test: ask *"Is this something the object **is/has**, or something it **does**?"*
- Is/has → **state**
- Does → **behavior**

---

## 3. Examples

### Dog (Buddy)
```
Object: Buddy (Dog)
  State:    name="Buddy", age=3, color="brown", hunger="very hungry"
  Behavior: bark(), eat(), sleep(), wag_tail()
```

### Cat (Luna)
```
Object: Luna (Cat)
  State:    fur_color="gray"
  Behavior: chase_laser()
```

### Smartphone
```
Object: Smartphone
  State:    battery_level=25
  Behavior: vibrate()
```

### Bank Account
```
Object: BankAccount
  State:    balance=500
  Behavior: deposit(), withdraw()
```

### Candle
```
Object: Candle
  State:    lit=True
  Behavior: melt()
```

---

## 4. Open-Note Review

**Key distinction**

| Example | State or Behavior? |
|---------|-------------------|
| Buddy's age is 3 | State |
| Buddy barks | Behavior |
| Luna's fur is gray | State |
| Luna chases a laser | Behavior |
| Battery level is 25% | State |
| The phone vibrates | Behavior |
| Balance is $500 | State |
| Withdraw $50 | Behavior |

**Quick self-test format**
```
Object: ___
  State:    ___, ___
  Behavior: ___(), ___()
```

---

## 5. Final Takeaway

Every OOP object bundles **state** (facts/data) and **behavior** (actions) into one unit. State answers *"what is it / what does it have?"* — behavior answers *"what can it do?"* This pairing is the foundation of everything else in OOP.

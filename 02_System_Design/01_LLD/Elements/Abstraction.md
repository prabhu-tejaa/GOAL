Using simple things to represent complexity.

To simply if, we all know how to turn on a car but we don't need to know how it works in order to drive the car.

**Abstraction** is about **simplicity** (hiding the complexity).

Abstraction is the process of hiding the internal details and showing only the essential features of an object. It focuses on **what** an object does instead of **how** it does it."

### The "Nice" Analogy: The Coffee Machine

Think about a coffee machine:

- **The Interface (Abstract):** You see a button that says "Espresso." You press it.
    
- **The Complexity (Hidden):** Inside, the machine is heating water, grinding beans, and building pressure.
    
- **The Point:** You don't need to know about the boiler or the grinder to get your coffee. You only interact with the **simple button**.

### Why use it?

- **Reduces Complexity:** You don't overwhelm other developers with 500 lines of internal logic; you just give them one simple method to call.
    
- **Easy Maintenance:** You can change the "internal grinder" of the coffee machine later, and as long as the "Espresso" button still works, the user doesn't have to change anything.

```
// 1. The "Abstract" Plan (The Blueprint)
abstract class CoffeeMachine {
    
    // The "What": Every machine MUST have a brew process
    public abstract void brew(); 

    // The "Hidden How": Common logic used internally
    protected void boilWater() {
        System.out.println("Boiling water at 90°C...");
    }
}

// 2. The "Concrete" Implementation (The Actual Machine)
class EspressoMachine extends CoffeeMachine {
    @Override
    public void brew() {
        boilWater(); // Use the hidden logic
        System.out.println("Using high pressure to make Espresso.");
    }
}

class DripCoffeeMaker extends CoffeeMachine {
    @Override
    public void brew() {
        boilWater(); // Use the hidden logic
        System.out.println("Dripping water slowly through filter.");
    }
}
```
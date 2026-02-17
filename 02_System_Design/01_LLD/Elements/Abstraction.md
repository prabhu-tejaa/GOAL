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
abstract class CoffeeMachine {
    
    public abstract void brew(); 

    protected void boilWater() {
        System.out.println("Boiling water at 90°C...");
    }
}

class EspressoMachine extends CoffeeMachine {
    @Override
    public void brew() {
        boilWater();
        System.out.println("Using high pressure to make Espresso.");
    }
}

class DripCoffeeMaker extends CoffeeMachine {
    @Override
    public void brew() {
        boilWater();
        System.out.println("Dripping water slowly through filter.");
    }
}

public class Main {
    public static void main(String[] args) {
        CoffeeMachine myMachine = new EspressoMachine();
        
        myMachine.brew(); 
    }
}
```

**Abstraction:** "I don't care how it works, just give me the result."

**Abstract Classes** and **Interfaces** are the two main ways to achieve Abstraction, but they do it in slightly different ways.

If an **Abstract Class** is a "Partial Blueprint" (some stuff is done, some isn't), an **Interface** is a **"Pure Contract."**

### The Interface (The "Pure" Abstraction)

An interface doesn't have any "how" at all. It only lists the commands. It's like a menu at a restaurant: it tells you **what** you can order, but it doesn't show you the kitchen.

#### The "Car" Example with Interface

Imagine a "Driver's License" contract. It doesn't matter if you drive a Truck or a Sedan; you must follow the same rules.

```
interface RemoteControl {
    void powerOn();
    void powerOff();
}

class TV implements RemoteControl {
    public void powerOn() {
        System.out.println("TV Screen is glowing...");
    }
    public void powerOff() {
        System.out.println("TV is shutting down.");
    }
}

class AirConditioner implements RemoteControl {
    public void powerOn() {
        System.out.println("AC fan is starting...");
    }
    public void powerOff() {
        System.out.println("AC compressor stopped.");
    }
}

public class Main {
    public static void main(String[] args) {
        RemoteControl myDevice;

        myDevice = new TV();
        myDevice.powerOn();

        myDevice = new AirConditioner();
        myDevice.powerOn();
    }
}
```


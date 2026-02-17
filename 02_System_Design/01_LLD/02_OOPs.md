## Object Oriented Programming System

>It is a programming style where we organize our code around **Real World Objects** instead of just a long list of functions. We bundle the **data** (what it is) and the **actions** (what it does) into one neat package called a **Class**."

###  4 Reasons why to use OOPs

- **Modularity for Easier Troubleshooting:** Since objects are self-contained, if something breaks in the "Payment" object, you know exactly where to look. You don't have to hunt through 5,000 lines of random code.
    
- **Code Reusability (Don't Repeat Yourself):** You can create a "Base" class and reuse it a million times. If you’ve defined what a `User` is, you don't have to rewrite that logic for an `Admin` or a `Customer`.

- **Scalability:** Easily add new features (like a "Premium User") by building on top of existing classes without rewriting the entire system.

- **Flexibility through Polymorphism:** You can use the same function name to do different things. This makes the code much cleaner and easier to read.
    
- **Effective Data Hiding:** Using encapsulation, you can protect sensitive data from being accidentally changed by other parts of the program.

### The "Real-World" Benefit

Imagine building a car.

- **Non-OOP:** You build the whole car as one giant, solid piece of metal. If the radio breaks, you have to scrap the whole car to fix it.
    
- **OOP:** The radio, the engine, and the wheels are all **separate objects**. If the radio breaks, you just unplug it and pop in a new one. The rest of the car keeps working fine.

Major elements in OOPS:
1. [[Encapsulation]]
2. [[Abstraction]]
3. [[Inheritance]]
4. [[Polymorphism]]
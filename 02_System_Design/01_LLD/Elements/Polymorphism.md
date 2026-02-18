Poly means many
morphism means form

Polymorphism means many forms
Same word to mean different things in different context.

**Keywords:**
method overloading
method overriding

It is often considered the most powerful pillar of OOP.

It allows one action to behave differently based on the object performing it.

**Example:**
A man at the same time is a Son, Father, Employee, Husband.
The same person possess different behavior at different different situations.

It allows us to perform single action in different different ways

There are two main types: 
**Static Polymorphism** (Compile time) and **Dynamic Polymorphism** (Runtime)

**Static Polymorphism** (Compile time) is what we call as **method overloading**
**Dynamic Polymorphism** (Runtime) is what we call as **method overriding** and there is another keyword for this **Dynamic method dispatch**

### **1. Static Polymorphism (Compile-time)**

- **Alternative Names:** Method Overloading, Early Binding.
    
- **How Java identifies it:** By the **Method Signature** (The method name + parameters).
    
- **The Rules:**
    
    - Methods must have the **same name**.
        
    - Methods must have **different parameters** (change in number of args, type of args, or order of args).
        
    - **Note:** Changing _only_ the return type is **not** overloading and will cause a compile error.
        
- **Real-world Logic:** Think of a **Search** function.
    
    - `search(String name)`
        
    - `search(int id)`
        
    - The "Script" (compiler) knows exactly which one to use the moment you type the input.

### **Dynamic Polymorphism (Runtime)**

- **Alternative Names:** Method Overriding, Late Binding, **Dynamic Method Dispatch**.
    
- **How Java identifies it:** By the **Object Type** created on the heap (using the `new` keyword).
    
- **The Rules:**
    
    - Requires **Inheritance** (`extends` or `implements`).
        
    - Methods must have the **exact same name and parameters**.
        
    - Uses the **`@Override`** annotation to signal intent.
        
- **The "Secret" (Upcasting):** This is where you use a Parent reference to point to a Child object.
    
    - `User u = new Student();`
        
    - `u.printRole();` -> Java waits until the app is running to see that `u` is actually a `Student`.

| **Feature**     | **Method Overloading**                                                                                   | **Method Overriding**                        |
| --------------- | -------------------------------------------------------------------------------------------------------- | -------------------------------------------- |
| **Concept**     | **Compile-time** (Static) Polymorphism.                                                                  | **Runtime** (Dynamic) Polymorphism.          |
| **Class**       | Occurs within the **same class**.                                                                        | Occurs between **Parent and Child** classes. |
| **Method Name** | Must be **the same**.                                                                                    | Must be **the same**.                        |
| **Parameters**  | Must be **different** (number, type, or order).                                                          | Must be **the exact same**.                  |
| **Return Type** | Can be different (Will not let you create two methods where the **only** difference is the return type). | Must be the **same** (or covariant).         |
| **Keywords**    | No special keyword used.                                                                                 | Uses the **`@Override`** annotation.         |

### **(The "3S" Rule)**

#### **1. Static vs. Dynamic**

- **Overloading** is **Static**: The compiler looks at the "Script" (your code) and decides which version to use before the app even starts.
    
- **Overriding** is **Dynamic**: The JVM (Java Virtual Machine) waits until the app is **Doing** something to see what the actual object is.
    

#### **2. Same vs. Sub (Inheritance)**

- **Overloading** happens in the **Same** class. You are just adding "flavors" to a method.
    
- **Overriding** requires a **Sub-class**. You are changing the behavior inherited from a parent.
    

#### **3. Signature vs. Logic**

- **Overloading** changes the **Signature** (the parameters).
    
- **Overriding** changes the **Logic** inside the body, keeping the signature identical.
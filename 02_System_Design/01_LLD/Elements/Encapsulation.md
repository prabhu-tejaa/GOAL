Wrapping data and methods into a single unit and hiding the internal state.

**Why?** 
To prevent outside code from accidentally corrupting data.

**Real-World Example:** 
A **Bank Account**. You can't change your `balance` directly; you have to use the `deposit()` or `withdraw()` methods.

We use the **`private`** access modifier to achieve Encapsulation. It hides the data so that it can only be accessed or modified through **public** methods, ensuring the data stays valid and secure.

```
## Where it CAN be changed
class BankAccount {
    private double balance;

    public void deposit(double amount) {
        balance = balance + amount; 
    }
}

## Where it CANNOT be changed
class Thief {
    public void hack(BankAccount account) {
        // ❌ ERROR: The compiler will stop you here.
        // "balance has private access in BankAccount"
        account.balance = 999999; 
    }
}
```

**Encapsulation** is about **security** (hiding the data)

**Encapsulation:** "Don't touch my stuff!" (Security/Grouping)

## Gemini said

That’s a great way to visualize it! To complete the picture of encapsulation and access control in Java, we can add **`protected`** and **`default`** (Package-Private) to your list.

Here is how you can expand your "security" analogy:

---

## The Encapsulation Security Levels

- **`private`** (The **Vault**): The "Lock." Prevents direct access from any other class. Only the owner (the class itself) has the key.
    
- **`default` / Package-Private** (The **Office Suite**): The "Keycard Access." Only people working in the same department (the same **package**) can walk in and see what's happening. Outsiders can't even see the door.
    
- **`protected`** (The **Family Inheritance**): The "Family Secret." Just like `default`, people in the same package can see it, but **subclasses** (the "children" of the class) also get a copy of the key, even if they move to a different city (package).
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

**`private`** The "Lock." Prevents direct access from other classes.
**Setters** The "Security Guard." Validates data before letting it in.
**Getters** The "View Window." Lets people see the data without touching it.
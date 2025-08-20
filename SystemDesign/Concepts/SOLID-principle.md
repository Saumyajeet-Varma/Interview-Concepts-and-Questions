# SOLID Principle

## S - Single Responsibility Principle (SRP)

A class should have **only one reason to change**. <br>
This means a class should focus on **one job** only.

#### Bad Example:

A class that handles both **user authentication** and **sending emails**. <br>
If email logic changes, you touch the same class that handles authentication → tightly coupled.

#### Good Example:

- `AuthService` → handles authentication.
- `EmailService` → handles email sending.

Now each class has **one responsibility**.

## O - Open/Closed Principle (OCP)

Classes should be **open for extension but closed for modification**. <br>
You should be able to add new functionality **without modifying existing code**.

#### Bad Example:

A `Payment` class has an `if-else` for `CreditCard`, `PayPal`, `UPI`. <br>
Adding a new method of payment → you must modify the class.

#### Good Example

- Create an interface `PaymentMethod`.
- Implement separate classes: `CreditCardPayment`, `PayPalPayment`, `UPIPayment`.
- The main `PaymentProcessor` just depends on the `PaymentMethod` interface.

Now adding a new payment type doesn’t touch existing code.

## L - Liskov Substitution Principle (LSP)

Objects of a superclass should be replaceable with objects of its subclasses **without breaking the program**.

#### Bad Example

- `Bird` class has `fly()`.
- `Penguin` inherits from `Bird` but **cannot fly** → violates LSP.

#### Good Example

- `Bird` → base class with common behavior.
- `FlyingBird` and `NonFlyingBird` → derived classes.

Now `Penguin` can extend `NonFlyingBird` and still follow LSP.

## Interface Segregation Principle (ISP)

A client should not be forced to implement interfaces it doesn’t use. <br>
Instead of one **fat interface**, create **smaller**, **specific ones**.

#### Bad Example

An interface `IMachine` with `print()`, `scan()`, `fax()`. <br>
If a simple printer implements it, it must define unnecessary methods like `fax()`.

#### Good Example

- `IPrinter` → has `print()`.
- `IScanner` → has `scan()`.
- `IFax` → has `fax()`.

Now classes implement only what they need.

## D - Dependency Inversion Principle (DIP)

Depend on **abstractions**, not on concrete implementations. <br>
High-level modules should not depend on low-level modules. Both should depend on **interfaces/abstractions**.

#### Bad Example

A `ReportGenerator` class directly uses `MySQLDatabase` to fetch data. <br>
Now, switching to `MongoDB` breaks things.

#### Good Example

- Create `Database` interface.
- `MySQLDatabase` and `MongoDBDatabase` implement it.
- `ReportGenerator` depends on `Database` interface, not the concrete DB.

Now you can swap databases easily.

## Summary of SOLID Principle

| Principle | Stands For            | Meaning                                              | Mnemonic                                                             |
| --------- | --------------------- | ---------------------------------------------------- | -------------------------------------------------------------------- |
| **S**     | Single Responsibility | One job per class                                    | One reason to change                                                 |
| **O**     | Open/Closed           | Extend without modifying existing code               | Open for extension, closed for modification                          |
| **L**     | Liskov Substitution   | Subclasses must be substitutable                     | Derived classes should work without breaking base class expectations |
| **I**     | Interface Segregation | Small, focused interfaces                            | Don’t force clients to depend on methods they don’t use              |
| **D**     | Dependency Inversion  | Depend on abstractions, not concrete implementations | High-level modules shouldn’t depend on low-level details             |

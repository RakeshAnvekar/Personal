# SOLID Principles in C#

A deep, interview-ready guide to mastering SOLID principles with C#
examples, real-world scenarios, and senior-level insights.

------------------------------------------------------------------------

## 📘 What is SOLID?

SOLID is a set of five object‑oriented design principles that help build
maintainable, scalable, and testable software.

  Letter   Principle
  -------- ---------------------------------
  S        Single Responsibility Principle
  O        Open Closed Principle
  L        Liskov Substitution Principle
  I        Interface Segregation Principle
  D        Dependency Inversion Principle

------------------------------------------------------------------------

# 1️⃣ Single Responsibility Principle (SRP)

> A class should have only one reason to change.

## ❌ Bad Example

``` csharp
public class InvoiceService
{
    public void CalculateTotal() { }
    public void SaveToDatabase() { }
    public void SendEmail() { }
}
```

Problems: - Multiple responsibilities - Hard to maintain - Hard to test

## ✅ Good Example

``` csharp
public class InvoiceCalculator
{
    public decimal CalculateTotal(Invoice invoice) { }
}

public class InvoiceRepository
{
    public void Save(Invoice invoice) { }
}

public class EmailService
{
    public void SendInvoiceEmail(Invoice invoice) { }
}
```

Benefits: - High cohesion - Easy testing - Clear separation of concerns

### 🎯 Interview Trap

SRP is **not** "one method per class".
It means **one responsibility**.

------------------------------------------------------------------------

# 2️⃣ Open Closed Principle (OCP)

> Open for extension, closed for modification.

## ❌ Bad Example

``` csharp
public class DiscountService
{
    public double GetDiscount(string customerType)
    {
        if (customerType == "Regular")
            return 0.1;
        else if (customerType == "Premium")
            return 0.2;
        return 0;
    }
}
```

## ✅ Good Example

``` csharp
public interface IDiscountStrategy
{
    double GetDiscount();
}

public class RegularCustomer : IDiscountStrategy
{
    public double GetDiscount() => 0.1;
}

public class PremiumCustomer : IDiscountStrategy
{
    public double GetDiscount() => 0.2;
}
```

Benefits: - Add new behavior without modifying old code - Supports
polymorphism

------------------------------------------------------------------------

# 3️⃣ Liskov Substitution Principle (LSP)

> **LSP:** Derived classes must be substitutable for their base classes
> without breaking behavior.


------------------------------------------------------------------------

## 🏦 Example 1 --- Payment Processing System

### ❌ Bad Design (LSP Violation)

``` csharp
public abstract class PaymentMethod
{
    public abstract void Pay(decimal amount);
    public virtual void Refund(decimal amount) { }
}

public class CreditCardPayment : PaymentMethod
{
    public override void Pay(decimal amount) { }
    public override void Refund(decimal amount) { }
}

public class CashOnDelivery : PaymentMethod
{
    public override void Pay(decimal amount) { }

    public override void Refund(decimal amount)
    {
        throw new NotSupportedException("Refund not supported");
    }
}
```

**Problem:**

``` csharp
void ProcessRefund(PaymentMethod payment)
{
    payment.Refund(100);
}

ProcessRefund(new CashOnDelivery()); // 💥 Runtime crash
```

`CashOnDelivery` cannot be safely substituted for `PaymentMethod`.

------------------------------------------------------------------------

### ✅ Good Design (LSP Compliant)

``` csharp
public abstract class PaymentMethod
{
    public abstract void Pay(decimal amount);
}

public interface IRefundable
{
    void Refund(decimal amount);
}

public class CreditCardPayment : PaymentMethod, IRefundable
{
    public override void Pay(decimal amount) { }
    public void Refund(decimal amount) { }
}

public class CashOnDelivery : PaymentMethod
{
    public override void Pay(decimal amount) { }
}
```

**Safe usage:**

``` csharp
void ProcessRefund(IRefundable payment)
{
    payment.Refund(100);
}
```

------------------------------------------------------------------------


------------------------------------------------------------------------

# 4️⃣ Interface Segregation Principle (ISP)

> Clients should not depend on methods they do not use.

## ❌ Bad Example

``` csharp
public interface IWorker
{
    void Work();
    void Eat();
}
```

## ✅ Good Example

``` csharp
public interface IWorkable
{
    void Work();
}

public interface IEatable
{
    void Eat();
}
```

------------------------------------------------------------------------

# 5️⃣ Dependency Inversion Principle (DIP)

> High-level modules should not depend on low-level modules.
> Both should depend on abstractions.

## ❌ Bad Example

``` csharp
public class OrderService
{
    private SqlOrderRepository _repository = new SqlOrderRepository();
}
```

## ✅ Good Example

``` csharp
public interface IOrderRepository
{
    void Save(Order order);
}

public class OrderService
{
    private readonly IOrderRepository _repository;

    public OrderService(IOrderRepository repository)
    {
        _repository = repository;
    }
}
```

------------------------------------------------------------------------

# 🧠 Senior-Level Insights

SOLID is about:

-   Reducing coupling
-   Increasing cohesion
-   Improving testability
-   Making systems easier to change

It is **not** about: - Creating too many classes - Over-engineering -
Adding interfaces everywhere

------------------------------------------------------------------------

# 🎯 Advanced Interview Questions (with Answers)

### Q1. Which SOLID principle is most violated in legacy code?

**SRP**

### Q2. Which principle helps most with unit testing?

**DIP**

### Q3. Which principle prevents fat interfaces?

**ISP**

### Q4. Which principle eliminates switch/if type logic?

**OCP**

### Q5. Which principle prevents runtime surprises?

**LSP**

### Q6. Can SOLID be applied without OOP?

Mostly no --- SOLID is rooted in object-oriented design.

### Q7. Does SRP mean one method per class?

No --- one responsibility per class.

### Q8. How does Dependency Injection relate to DIP?

DI is a technique that helps implement DIP.

### Q9. Is inheritance required for OCP?

No --- interfaces and composition work too.

### Q10. Which principle improves maintainability the most?

SRP + DIP together.

------------------------------------------------------------------------

# 🏗️ Real-World .NET Architecture Using SOLID

## Example: Payment Processing System

### Components:

-   Payment Service
-   Notification Service
-   Logging Service
-   Caching Layer
-   Repository Layer


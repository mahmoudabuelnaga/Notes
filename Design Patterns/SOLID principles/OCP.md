# Open/Closed Principle (OCP)

This principle aims to allow software systems to be extendable without modifying the existing code, thus reducing the risk of introducing new bugs into the existing system.

The Open/Closed Principle (OCP) is one of the five SOLID principles of object-oriented design, which is intended to make software designs more manageable, flexible, and scalable. The principle was introduced by Bertrand Meyer in 1988 and is defined as:

> "Software entities (classes, modules, functions, etc.) should be open for extension, but closed for modification."

This means that a software entity should allow its behavior to be extended without modifying its source code. The principle aims to promote the development of systems that are easy to extend over time and encourages the minimization of changes to existing code, which can introduce risks and errors.

## Why OCP Matters

- **Minimize Risk**: Changing existing code can introduce bugs in parts of the system that were previously working correctly. By extending without modifying, you minimize the risk of introducing new bugs.
- **Enhance Reusability**: By designing modules that can be extended, you can reuse existing functionality and extend it in new contexts.
- **Improve Maintainability**: Systems designed with OCP in mind are easier to maintain since new functionality can be added with minimal changes to the existing code.

## How to Apply OCP

Applying the Open/Closed Principle typically involves the use of interfaces or abstract classes to define contracts for modules. Concrete implementations can then extend these abstract entities without changing their original code. Here's how you can apply OCP:

1. **Use Abstraction**: Define abstract classes or interfaces that represent the behaviors that are subject to change or extension. 
2. **Implement with Extension**: When you need to add new functionality, introduce new classes that implement the interfaces or inherit from the abstract classes without altering the existing implementations.
3. **Invert Dependencies**: Depend on abstractions rather than concrete implementations. This can be achieved using techniques like dependency injection, which further decouples the system components.

## Example

Imagine you have a system that processes payments, and initially, it only needs to handle credit card payments. According to OCP, you should design the system so that adding new payment methods in the future doesn't require modifying the existing payment processing code.

- Start with an interface `PaymentProcessor` that defines a method `processPayment(amount)`.
- Implement this interface with a class `CreditCardProcessor` to handle credit card payments.
- Later, if you need to add support for digital wallets, you can create a new class `DigitalWalletProcessor` that also implements the `PaymentProcessor` interface. 

This way, the system can support new payment methods without modifying the existing payment processing code, adhering to the Open/Closed Principle.

Consider a scenario where we have a system that filters products by different criteria. To adhere to the OCP, we can define a generic interface for a specification and then extend it for specific criteria.

### Before Applying OCP

```python
class Product:
    def __init__(self, name, color, size):
        self.name = name
        self.color = color
        self.size = size

class ProductFilter:
    def filter_by_color(self, products, color):
        for p in products:
            if p.color == color:
                yield p

    # Suppose we want to add a new filter criterion, size.
    # Following this approach would require us to modify the ProductFilter class,
    # which violates the Open/Closed Principle.
```

### After Applying OCP

```python
from abc import ABC, abstractmethod

class Specification(ABC):
    @abstractmethod
    def is_satisfied(self, item):
        pass

class ColorSpecification(Specification):
    def __init__(self, color):
        self.color = color

    def is_satisfied(self, item):
        return item.color == self.color

class SizeSpecification(Specification):
    def __init__(self, size):
        self.size = size

    def is_satisfied(self, item):
        return item.size == self.size

class BetterFilter:
    def filter(self, items, spec):
        for item in items:
            if spec.is_satisfied(item):
                yield item
```

In this Python example, we have created a system where adding new filtering criteria does not require any changes to existing code. Instead, we extend the system by adding new specifications.

## Java Example

Consider a logging system where the log output can be sent to different outputs (console, file, etc.). To adhere to the OCP, we define an interface for logging and then extend it for specific outputs.

### Before Applying OCP

```java
public class Logger {
    public void log(String message) {
        // Log to console
        System.out.println(message);
        // What if we now want to log to a file or send an email?
        // Adding those capabilities would require modifying this class.
    }
}
```

### After Applying OCP

```java
interface LogStrategy {
    void log(String message);
}

class ConsoleLogStrategy implements LogStrategy {
    @Override
    public void log(String message) {
        System.out.println(message);
    }
}

class FileLogStrategy implements LogStrategy {
    @Override
    public void log(String message) {
        // Logic to log to a file
    }
}

public class Logger {
    private LogStrategy logStrategy;

    public Logger(LogStrategy logStrategy) {
        this.logStrategy = logStrategy;
    }

    public void log(String message) {
        logStrategy.log(message);
    }
}
```
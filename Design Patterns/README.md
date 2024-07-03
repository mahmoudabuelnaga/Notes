## Design Patterns

Design patterns are typical solutions to common problems in software design. They are not finished designs that can be directly transformed into code but rather templates for how to solve problems that can be used in many different situations. Each pattern describes a problem that occurs frequently in our environment, along with a core solution to that problem, which is both reusable and adaptable.

### Categories of Design Patterns

#### 1. Creational Patterns
These patterns provide ways to instantiate objects, ensuring that the creation process is managed in a way that suits the situation. Examples include:

- **Singleton**: Ensures a class has only one instance and provides a global point of access to it.
- **Factory Method**: Defines an interface for creating an object but allows subclasses to alter the type of objects that will be created.
- **Abstract Factory**: Provides an interface for creating families of related or dependent objects without specifying their concrete classes.
- **Builder**: Separates the construction of a complex object from its representation so that the same construction process can create different representations.
- **Prototype**: Specifies the kinds of objects to create using a prototypical instance and creates new objects by copying this prototype.

#### 2. Structural Patterns
These patterns deal with object composition or how classes and objects are composed to form larger structures. Examples include:

- **Adapter**: Allows the interface of an existing class to be used as another interface.
- **Decorator**: Adds responsibilities to objects dynamically.
- **Facade**: Provides a simplified interface to a complex subsystem.
- **Proxy**: Provides a surrogate or placeholder for another object to control access to it.
- **Composite**: Composes objects into tree structures to represent part-whole hierarchies.
- **Bridge**: Decouples an abstraction from its implementation so that the two can vary independently.

#### 3. Behavioral Patterns
These patterns are concerned with algorithms and the assignment of responsibilities between objects. Examples include:

- **Observer**: Defines a one-to-many dependency between objects so that when one object changes state, all its dependents are notified and updated automatically.
- **Strategy**: Defines a family of algorithms, encapsulates each one, and makes them interchangeable.
- **Command**: Encapsulates a request as an object, thereby allowing for parameterization of clients with queues, requests, and operations.
- **Chain of Responsibility**: Passes a request along a chain of handlers, where each handler decides whether to process the request or pass it on to the next handler.
- **Mediator**: Defines an object that encapsulates how a set of objects interact.
- **State**: Allows an object to alter its behavior when its internal state changes.

Using design patterns can lead to more flexible, reusable, and maintainable code. They are a way of thinking about and solving problems that can be adapted to various programming languages and paradigms.

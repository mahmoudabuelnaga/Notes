The Interface Segregation Principle (ISP) is one of the five core principles of SOLID, aimed at creating more maintainable and flexible software designs. It was introduced by Robert C. Martin and emphasizes the importance of creating lean and focused interfaces.

## Interface Segregation Principle (ISP)

ISP states that:

> No client should be forced to depend on methods it does not use.

This principle suggests that rather than having one large interface, it's better to have several smaller interfaces, each tailored to specific client needs. This approach prevents a class from being forced to implement interfaces and methods it does not use, leading to cleaner, more understandable, and easier to manage code.

## Why Interface Segregation Principle Matters

- **Reduces Bloat**: Ensures that classes don't carry unnecessary methods that they don't need, reducing the overhead and potential for confusion.
- **Enhances Cohesion**: By focusing on specific interfaces, classes become more cohesive and focused on their intended purposes.
- **Increases Reusability**: Smaller, more focused interfaces are easier to implement and reuse across different parts of an application.
- **Improves Maintainability**: With fewer dependencies on unused interfaces, the system becomes easier to maintain and evolve over time.

## Examples

### Example in Java

Imagine a multimedia application that handles music and video playback. Using a single interface for both functionalities might force some classes to implement methods they don't need.

```java
interface Multimedia {
    void playAudio();
    void playVideo();
}
```

A class that only handles audio playback would still need to implement `playVideo()`, which it doesn't need, violating ISP.

A better approach would be to segregate the `Multimedia` interface into two separate interfaces:

```java
interface AudioPlayer {
    void playAudio();
}

interface VideoPlayer {
    void playVideo();
}
```

Now, classes can implement only the interfaces that are relevant to them, adhering to ISP.

### Example in Python

Consider a smart home system where devices like lights and thermostats are controlled via a common interface. Initially, you might design it like this:

```python
class SmartDevice:
    def turn_on(self): pass
    def turn_off(self): pass
    def set_temperature(self, temperature): pass
```

However, not all smart devices will have a temperature setting (e.g., lights), making the `set_temperature` method irrelevant for some implementations.

Adhering to ISP, you would refactor this into more focused interfaces:

```python
class Switchable:
    def turn_on(self): pass
    def turn_off(self): pass

class TemperatureControl:
    def set_temperature(self, temperature): pass
```

This way, a light can implement `Switchable` without being forced to implement `TemperatureControl`, which it doesn't need, thus following the Interface Segregation Principle.

The Interface Segregation Principle encourages the design of small, focused interfaces that are specifically tailored to the needs of their clients. By adhering to ISP, developers can create more modular, maintainable, and flexible software systems that are easier to understand and evolve over time.
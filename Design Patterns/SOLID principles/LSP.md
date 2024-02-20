# Liskov Substitution Principle (LSP)

The Liskov Substitution Principle (LSP) is one of the five SOLID principles of object-oriented design, which guides developers in creating more maintainable, scalable, and robust systems. Introduced by Barbara Liskov in a 1987 conference, the principle is formally defined as:

- > Objects in a program should be replaceable with instances of their subtypes without altering the correctness of the program.
- > "Let \(q(x)\) be a property provable about objects \(x\) of type \(T\). Then \(q(y)\) should be provable for objects \(y\) of type \(S\) where \(S\) is a subtype of \(T\)."

In simpler terms, the Liskov Substitution Principle states that objects of a superclass should be replaceable with objects of its subclasses without affecting the correctness of the program. This means that a subclass should fully implement the interface of its superclass so that it can stand in for its superclass without altering the desirable properties of the program (correctness, task performed, etc.).

## Why LSP Matters

- **Reliability**: Adhering to LSP ensures that a program remains correct and reliable when a subclass instance replaces a superclass instance.
- **Reusability**: It enhances the reusability of subclasses, allowing them to be used wherever their superclass is expected.
- **Maintainability**: Code is easier to maintain because the hierarchy is logically consistent, and subclasses behave as expected from the perspective of a superclass user.

## How to Apply LSP

To adhere to the Liskov Substitution Principle, ensure that:

1. **Subclasses Don't Weaken Preconditions**: Subclasses should not enforce stricter conditions than those of the superclass for method inputs.
2. **Subclasses Don't Strengthen Postconditions**: The outcomes of subclass methods should meet or exceed the specifications of the superclass methods.
3. **Subclasses Maintain Invariants**: Subclasses should maintain any invariants defined by the superclass, ensuring that the system remains in a valid state.
4. **Exceptions Are Consistent**: Subclasses should not introduce new exceptions that could be unexpected from the perspective of the superclass's clients.

## Example

Consider a class `Bird` with a method `fly()`. If you have a subclass `Duck` that inherits from `Bird`, it's logical for `Duck` to implement `fly()` because ducks can fly. However, if you introduce a subclass `Penguin` which also inherits from `Bird`, it would violate LSP to implement `fly()` in the same way since penguins cannot fly. This scenario indicates a design problem where the superclass and subclasses are not correctly aligned according to LSP.

A solution could involve refactoring the hierarchy to have a more general superclass (e.g., `Animal`), from which `Bird` and `Penguin` inherit, and introducing an interface `Flyable` for classes like `Duck`.

### Python Example

Consider a scenario where you have a class `Bird` with a method `fly()`. Not all birds can fly (e.g., penguins), so making a subclass `Penguin` that inherits `Bird` and overrides `fly()` might violate LSP if the `fly()` method is called expecting all `Bird` objects to fly.

```python
class Bird:
    def fly(self):
        print("This bird can fly.")

class Penguin(Bird):
    def fly(self):
        raise Exception("This bird cannot fly.")

def make_bird_fly(bird: Bird):
    bird.fly()

eagle = Bird()
make_bird_fly(eagle)  # Works fine

penguin = Penguin()
make_bird_fly(penguin)  # Raises Exception, violating LSP
```

A better approach that adheres to LSP would be to refactor the hierarchy, possibly by introducing more abstract classes/interfaces or segregating the functionality:

```python
class Bird:
    pass

class FlyingBird(Bird):
    def fly(self):
        print("This bird can fly.")

class NonFlyingBird(Bird):
    pass

class Eagle(FlyingBird):
    pass

class Penguin(NonFlyingBird):
    pass
```

### Java Example

In Java, consider a class `Rectangle` and a subclass `Square`. A square is a type of rectangle where the width and height are equal, but if setting the width or height independently leads to unexpected behavior for a `Square` object, it may violate LSP.

```java
class Rectangle {
    protected int width, height;

    public void setWidth(int width) {
        this.width = width;
    }

    public void setHeight(int height) {
        this.height = height;
    }

    public int getArea() {
        return width * height;
    }
}

class Square extends Rectangle {
    @Override
    public void setWidth(int width) {
        super.setWidth(width);
        super.setHeight(width);
    }

    @Override
    public void setHeight(int height) {
        super.setWidth(height);
        super.setHeight(height);
    }
}
```

Using a `Square` object in place of a `Rectangle` could lead to unexpected results, especially if the client code depends on independently setting the width and height of a `Rectangle`.

A solution to adhere to LSP might involve rethinking the inheritance hierarchy or introducing interfaces to better represent the behaviors:

```java
interface Shape {
    int getArea();
}

class Rectangle implements Shape {
    private int width, height;

    public Rectangle(int width, int height) {
        this.width = width;
        this.height = height;
    }

    @Override
    public int getArea() {
        return width * height;
    }
}

class Square implements Shape {
    private int sideLength;

    public Square(int sideLength) {
        this.sideLength = sideLength;
    }

    @Override
    public int getArea() {
        return sideLength * sideLength;
    }
}
```
# Single Responsibility Principle (SRP)

The Single Responsibility Principle (SRP) states that a class should have only one reason to change, meaning it should have only one job or responsibility. This principle is a part of the SOLID principles, which guide object-oriented design and programming for better software development practices.

The Single Responsibility Principle (SRP) is one of the core concepts of the SOLID principles, aimed at making software more maintainable and understandable. Formulated by Robert C. Martin, SRP states that:

> "A class should have one, and only one, reason to change."

This principle suggests that a class should be tasked with a single responsibility or concern. If a class is handling multiple responsibilities, it becomes tightly coupled and harder to maintain. Changes to one responsibility may affect the class's ability to fulfill its other responsibilities, leading to a fragile design that is difficult to understand, modify, or extend.

## Why SRP Matters

- **Maintainability**: Classes with a single responsibility are easier to understand and maintain because they have a clear, well-defined purpose.
- **Testability**: It's easier to test a class that has a single responsibility. The tests are more focused and less likely to require changes unless there's a change in the responsibility itself.
- **Flexibility and Reusability**: Classes that focus on a single responsibility can be more easily reused or changed since their functionality is isolated.
- **Reduced Coupling**: Following SRP leads to decreased coupling between classes. Each class is independent and interacts with other classes through well-defined interfaces.

## How to Apply SRP

To apply SRP, start by identifying the different responsibilities within a class. Responsibilities are reasons for change; if you can think of more than one motive for modifying a class, it likely violates SRP. Once identified, these responsibilities should be separated into their own classes, ensuring that each class deals with only one concern.

## Example

Consider a class that manages employee data in a company. If this class is responsible for both storing employee information and generating reports about employees, it violates SRP because it has two reasons to change: changes to how employee information is stored and changes to the report formats or contents.

To adhere to SRP, you would split this into two classes:
- An `EmployeeManager` class responsible for managing employee information.
- An `EmployeeReportGenerator` class responsible for generating reports about employees.

This separation ensures that changes to the report generation logic don't affect the employee management logic and vice versa, adhering to the Single Responsibility Principle.

### SRP in Python:

Consider a class that violates the SRP by handling both user data management and user notification responsibilities:

```python
class UserManager:
    def __init__(self, user):
        self.user = user

    def change_user_address(self, new_address):
        self.user.address = new_address
        self._send_user_notification(self.user)

    def _send_user_notification(self, user):
        print(f"Notification sent to {user.name}.")

# Usage
user = UserManager(User("John Doe", "123 Main St"))
user.change_user_address("456 Elm St")
```

To adhere to SRP, we should refactor this by splitting the responsibilities into two classes: one for managing the user and another for handling notifications.

```python
class User:
    def __init__(self, name, address):
        self.name = name
        self.address = address

class UserManager:
    def __init__(self, user):
        self.user = user

    def change_user_address(self, new_address):
        self.user.address = new_address

class UserNotifier:
    @staticmethod
    def send_user_notification(user):
        print(f"Notification sent to {user.name}.")

# Usage
user = User("John Doe", "123 Main St")
user_manager = UserManager(user)
user_notifier = UserNotifier()

user_manager.change_user_address("456 Elm St")
user_notifier.send_user_notification(user)
```

### SRP in Java:

Similarly, in Java, let's illustrate a class that violates the SRP by having multiple responsibilities:

```java
public class UserManager {
    private User user;

    public UserManager(User user) {
        this.user = user;
    }

    public void changeUserAddress(String newAddress) {
        user.setAddress(newAddress);
        sendUserNotification(user);
    }

    private void sendUserNotification(User user) {
        System.out.println("Notification sent to " + user.getName() + ".");
    }
}
```

Refactoring for SRP would involve creating separate classes for user management and notifications:

```java
public class User {
    private String name;
    private String address;

    // Constructor, getters and setters
}

public class UserManager {
    private User user;

    public UserManager(User user) {
        this.user = user;
    }

    public void changeUserAddress(String newAddress) {
        user.setAddress(newAddress);
    }
}

public class UserNotifier {
    public static void sendUserNotification(User user) {
        System.out.println("Notification sent to " + user.getName() + ".");
    }
}

// Usage
User user = new User("John Doe", "123 Main St");
UserManager userManager = new UserManager(user);
UserNotifier.sendUserNotification(user);
```

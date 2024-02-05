# Spring Framework Overview
## Goals of Spring:
1. Utilizes Java POJOs for simpler and lightweight development, avoiding the complexities of early J2EE's EJBs.
2. Promotes loose coupling through dependency injection, allowing object relationships to be defined via configuration files or annotations.
3. Aims to minimize Java boilerplate code, leveraging Spring's helper classes to streamline development.

## Core Containers:
![alt text](<Images/ages/Screenshot from 2024-02-04 19-39-30.png>)
The Spring Core Container is a fundamental part of the Spring Framework, providing the primary functionality for managing Spring beans. Beans are objects that form the backbone of your application and are managed by the Spring IoC (Inversion of Control) container. The Core Container is responsible for instantiating, configuring, and assembling these beans through dependency injection.

The Spring Core Container itself is made up of several modules, including:

1. **Spring Core**: This module provides the fundamental parts of the framework, including the IoC and Dependency Injection features. It's responsible for managing beans and injecting dependencies through either constructor or setter methods.

2. **Spring Bean**: This module handles the configuration and management of Spring beans. It uses the `BeanFactory` interface, which provides an advanced configuration mechanism capable of managing any type of object.

3. **Spring Context**: This module builds on the solid base provided by the Core and Beans modules. It is a medium for accessing any objects defined and configured. The ApplicationContext interface is the focal point of the Context module, offering a more feature-rich extension to the BeanFactory.

4. **Spring Expression Language (SpEL)**: This module provides a powerful expression language for querying and manipulating an object graph at runtime. It is used for setting bean properties and supports advanced features like calling methods, accessing properties, and calling constructors.

These components work together to form the Spring Core Container, offering a comprehensive and modular framework for building and managing the lifecycle of beans in your application. Dependency Injection (DI) is a central concept in Spring, allowing for loose coupling of components and easier testability.

## Infrastructure:
![alt text](<Images/Screenshot from 2024-02-04 20-21-07.png>)
1. **Aspect-Oriented Programming (AOP) Support:** AOP allows for the implementation of application-wide services such as logging, security, transactions, and instrumentation.
2. **Declarative Service Application:** Services can be applied to objects in a declarative manner, without the need for modifying the code.
3. **Configuration-based Implementation:** Services are enabled through configurations in a config file or annotations, facilitating their integration into the application.
4. **Practical Applications:** Examples of AOP will be demonstrated, especially in the context of transactions, among other areas.

## Data Access Layer:
![alt text](<Images/Screenshot from 2024-02-04 20-17-06.png>)
1. **Data Access/Integration**: Focuses on communicating with databases (both relational and NoSQL) and using message queues.
2. **JDBC Support**: Spring offers helper classes that simplify database access via JDBC, potentially reducing source code by more than 50%.
3. **ORM (Object-Relational Mapping)**: A key feature that integrates with Hibernate or JPA, showcasing strong support and synergy between Spring and ORM frameworks.

# What is Maven:
## What is Maven?
- Maven is a project management tool.
- So the most popular use of Maven is for build management and dependencies.

## what problems does Maven solve?
- when you're building your Java project, you may need additional JAR files like Spring JAR files, Hibernate JAR files, so on.
- And one approach is to simply download those JAR files from each project website.
- Manually add those JAR files to your build path or class path.

## my project would work without Maven:
Summary of the key points regarding managing a project without Maven:

1. **Manual Dependency Management**: Without Maven, you would need to manually handle dependencies such as Spring, Hibernate, Commons Logging, and any libraries needed for JSON processing. This involves visiting each project's website to download the required JAR files.

2. **Manual Addition to Build Path**: After downloading, you must manually add these JAR files to your project's build path to integrate them into your development environment.

3. **Maven's Role**: Maven simplifies this process by automating the dependency management and integration, significantly reducing the manual effort involved in setting up and maintaining these libraries in your project.


## Maven solution: 
1. Maven manages project dependencies such as Spring and Hibernate.
2. Automatically downloads necessary JAR files from the internet.
3. Makes JAR files accessible during both compile time and runtime.
4. Acts as a personal assistant for managing and acquiring project dependencies.

## My Project with Maven:
![alt text](<Images/Screenshot from 2024-02-05 15-38-49.png>)
1. **Use of Maven Central Repository:** Maven accesses a remote repository on the internet to find the necessary libraries.

2. **Project Dependencies Management:** Developers provide Maven with a "shopping list" (dependencies needed for the project, such as Spring, Hibernate, Commons, JSON, etc.).

3. **Automatic Download and Integration:** Maven automatically downloads the specified JAR files and makes them available on the developer's computer.

4. **Efficiency and Convenience:** This process allows developers to focus on coding rather than manually managing libraries, enhancing productivity and convenience.
All righty, so let's go ahead and dive in.

## Maven - How it works?
![alt text](<Images/Screenshot from 2024-02-05 16-41-39.png>)
1. **Configuration Reading**: Maven starts by reading the project configuration file, which serves as a "shopping list" for what's needed.
2. **Local Repository Check**: It first checks the Maven Local Repository on the user's computer, acting as a local cache for required files.
3. **Remote Fetching**: If the needed files are not found locally, Maven fetches them from the Maven Central Repository on the internet.
4. **Caching and Building**: Downloaded files are saved in the local repository, enriching the local cache for future use. Maven then utilizes these files to build and run the application.

## Handling JAR Dependencies:
1. Maven automatically retrieves project dependencies during the build process.
2. It also supports and manages transitive dependencies, such as how Spring Framework depends on commons-logging.
3. This dependency management is handled by Maven without the need for manual intervention.

## Building and Running:
1. **Dependency Management**: Maven automatically resolves and downloads project dependencies.
2. **Automated Build and Run**: Handles class and build path configurations based on the Maven configuration file, eliminating the need for manual setup.
3. **Efficiency**: Simplifies project setup and management, freeing up time for other activities.
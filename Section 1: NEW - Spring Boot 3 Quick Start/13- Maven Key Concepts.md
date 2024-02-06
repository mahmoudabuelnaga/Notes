# Maven Key Concepts
## POM file - pom.xml
- **Introduction to POM File**: The POM (Project Object Model) file serves as the configuration file for a project, guiding Maven on the dependencies the project requires. It acts like a "shopping list" for Maven.
- **Location**: The POM file is always found at the root of a Maven project.
- **Project Coordinates**: Discussion will include how project coordinates are utilized within the POM file to manage dependencies and project specifications.

## POM File Structure
The POM (Project Object Model) file structure in Maven includes the following key components:
1. **Project Metadata**: This section contains information about your project, including its name, version number, and the type of output file (e.g., JAR, WAR).
2. **Dependencies**: Specifies the external projects or libraries that your project depends on, such as Spring, Hibernate, or JSON libraries.
3. **Plugins**: Lists additional tasks or custom functionalities that can be executed, such as generating JUnit test reports.

## Project Coordinates
Here's a summarized version of the explanation about project coordinates:

1. **Unique Identification**: Project coordinates uniquely identify a project, analogous to how GPS coordinates identify a specific location like a house.
   
2. **Components**: The system uses three main components similar to an address system:
   - **Group ID**: Comparable to the city, usually the company, group, or organization name, following the convention of using a reversed domain name (e.g., `com.luv2code`).
   - **Artifact ID**: Similar to the street, it's the specific name of the project.
   - **Version**: Acts like the house number, indicating the project's specific release version (e.g., `1.0`, `1.6`, `2.0`). A version ending in `-SNAPSHOT` indicates active development.

3. **Convention and Examples**: The naming convention for these coordinates follows that used for Java package naming, focusing on clarity and specificity. Examples include dependencies for well-known projects like Spring and Hibernate, each defined by their group ID, artifact ID, and version.

4. **Purpose and Use**: These coordinates are essential in the Maven world for identifying and managing project dependencies, ensuring precise project identification and dependency management.

## Adding dependencies
1. To add Spring and Hibernate support to a project, dependencies for these frameworks need to be specified in the project's dependency section.
2. The dependencies include `spring-context` for the Spring framework and `hibernate-core` for Hibernate.
3. Maven is used to manage these dependencies, acting as a "shopping list" to automatically download the necessary JAR files from the internet for use in the application.

## Dependency Coordinates
1. To add a dependency to a project, you need the Group ID and Artifact ID; the Version is optional but highly recommended for repeatable builds.
2. Including the version number is considered a best practice in DevOps to ensure that the project works with a specific, tested, and verified version of a dependency.
3. This practice helps maintain consistency and reliability in project builds.
4. The acronym GAV stands for Group ID, Artifact ID, and Version, which you might encounter in documentation or discussions among Java developers, referring to the components needed for specifying dependencies.

## How to find Dependency Coordinates?
1. **Visit the Project Page:** You can find the necessary details to add these projects using Maven by visiting their respective websites (Spring or Hibernate).
   
2. **Use the Maven Central Repository:** An easier approach for finding dependency details is to search directly on the Maven Central Repository (search.maven.org), which serves as a one-stop shop for retrieving Maven coordinates for multiple dependencies.

** The second option is highlighted as the most convenient, especially for larger projects with numerous dependencies, as it avoids the need to visit each project's website individually.**
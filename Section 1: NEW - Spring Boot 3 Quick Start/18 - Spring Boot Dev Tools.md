# Spring Boot Dev Tools
## The Problem:
- When running Spring Boot Applications:
    - if you make changes to your source code.
    - Then you have to manully restart your application.

## The Solution:
- Spring-boot-devtools to the rescue!
- Automatically restarts your application when code is updated
- Simply add the dependency to your POM file.
- No need to write additional code
- For IntelliJ, need to set additional configurations

## Development Process
1. Apply IntelliJ configurations:
    - 1<sub>st</sub> Step:
        1. Select: Preferences or Settings >> Build, Execution, Development >> Compiler
        2. Check box: **Build Project Automatically**
    
    - 2<sub>nd</sub> Step (Additional Settings):
        1. Select: Preferences or Settings >> Advanced Settings
        2. Check box: **Allow auto-make to start even if developed is currently running**

    
2. Edit pom.xml and add spring-boot-devtools:
    ```xml
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-devtools</artifactId>
        </dependency>
    ```
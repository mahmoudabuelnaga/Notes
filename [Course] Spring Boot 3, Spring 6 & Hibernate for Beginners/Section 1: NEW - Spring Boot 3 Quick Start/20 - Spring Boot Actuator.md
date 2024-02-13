# Spring Boot Actuator 
## Problem:
- How can I monitor and manage y application?
- How can I check the application heahlth / status?
- How can I access application metrics?

## Solution: Spring Boot Actuator
- Exposes endpoint to monitor and manage your application.
- You easily get DevOps functionality out-of-the-box.
- Simply add the dependency to your POM file.
- REST endpoints are automatically added to your application.
> No need to write additional code! You get new REST endpoints for FREE!

## Spring Boot Actuator
- Adding the dependency to your POM file:
    ```xml
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-actuator</artifactId>
    </dependency>
    ```
- Automatically exposes endpoints for metrics out-of-the-box
- Endpoints are prefixed with: `/actuator`:
    | Name | Description |
    |------|-------------|
    | /health | Health information about your application. |
    | ....... | ........ |

## Health Endpoint:
- `/health` checks the status of your application.
- Normally used by monitoring apps to see if your app is up or down.
- This health status is customizable, so you can actually customize this based on your own custom business logic.
![alt text](<Images/Screenshot from 2024-02-11 14-50-26.png>)

## Exposing Endpoints:
- By default, only `/health` is exposed.
- The `/info` endpoint can provide information about your application, To expose `/info`:
    - go to the File: `application.properties`
    - add this line in it: 
        - `management.endpoints.web.exposure.include=health, info`
        - `management.info.env.enabled=true`

## Info Endpoint:
- `/info` gives information about your application.
- Default is empty:![alt text](<Images/Screenshot from 2024-02-11 17-13-41.png>)
- Update `application.properties` with your app info.
    - `info.{key}={value}`
    - best practices: `info.app.{key}={value}`
        - For Example:
            - `info.app.name=Naga App`
            - `info.app.description=Description for Naga App`
            - `info.app.version=1.0.0`
            - `info.app.my_birthday=20 Muharram`

## Spring Boot Actuator Endpoints:
> There are more Sring Boot Actuator endpoints.

| Name | Description |
|------|-------------|
| /auditevevnts | Audit evevnts for your application, or lists security audit-related events such as user login/logout. Also, we can filter by principal or type among other fields. |
| /beans | returns all available beans in our BeanFactory. Unlike /auditevents, it doesn’t support filtering. |
| /conditions | formerly known as /autoconfig, builds a report of conditions around autoconfiguration. |
| /configprops | allows us to fetch all @ConfigurationProperties beans. |
| /env | returns the current environment properties. Additionally, we can retrieve single properties. |
| /flyway | provides details about our Flyway database migrations. |
| /health | summarizes the health status of our application. |
| /heapdump |  |
| /auditevevnts | builds and returns a heap dump from the JVM used by our application. |
| /info | returns general information. It might be custom data, build information or details about the latest commit. |
| /liquibase | behaves like /flyway but for Liquibase. |
| /logfile | returns ordinary application logs. |
| /loggers | enables us to query and modify the logging level of our application. |
| /metrics | details metrics of our application. This might include generic metrics as well as custom ones. |
| /prometheus | returns metrics like the previous one, but formatted to work with a Prometheus server. |
| /scheduledtasks | provides details about every scheduled task within our application. |
| /sessions | lists HTTP sessions, given we are using Spring Session. |
| /shutdown | performs a graceful shutdown of the application. |
| /threaddump | dumps the thread information of the underlying JVM. |
| /mappings | List of all @RequestMapping paths. |

> For more details: [Spring Docs](https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#actuator.endpoints), [Spring Boot Actuator](https://www.baeldung.com/spring-boot-actuators)

## Exposing Endpoints:
- By default, only /health is exposed.
- To expose all actuator endpoints over HTTP:
    - go to the application.properties file, and add this line:
        - `management.endpoints.web.exposure.include=*`


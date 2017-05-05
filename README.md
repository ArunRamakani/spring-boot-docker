# Spring Boot Docker with Alpine Linux + Oracle Java 8

[![](https://images.microbadger.com/badges/image/flopes/spring-boot-docker.svg)](https://microbadger.com/images/flopes/spring-boot-docker "Get your own image badge on microbadger.com")

[![](https://img.shields.io/docker/pulls/flopes/spring-boot-docker.svg)](https://img.shields.io/docker/pulls/flopes/spring-boot-docker.svg)
[![](https://img.shields.io/docker/stars/flopes/spring-boot-docker.svg)](https://img.shields.io/docker/stars/flopes/spring-boot-docker.svg)

Features:
- Oracle Java 8 
- Spring profiles
- Custom JAVA_OPTS
- Wrapper script that enables application to take PID 1 & receive SIGTERM signals
- Health check (Docker tag `1.0-healthcheck` https://github.com/f-lopes/spring-boot-docker/tree/healthcheck)
- Debug mode

## Available environment variables

Name                    | Default   | Description
------------------------|-----------|------------------------------------
SPRING_PROFILES_ACTIVE  | dev   | Active Spring profiles
JAVA_OPTS               |       | JAVA_OPTS
DEBUG                   | false | Enable or disable debug mode
DEBUG_PORT              | 8000  | Debug port


## How to use ?

1. Simply extend your image from `flopes/spring-boot-docker` and set your application name as an environment variable:
    ``` Docker
    FROM flopes/spring-boot-docker:1.0
    
    ENV ARTIFACT_NAME my-spring-boot-application.jar
    ```

2. Copy your Spring Boot executable jar into an `assets` folder and build you image:
```docker build -t spring-boot-image . ```

3. Start your application:
    - Using Docker CLI

    - Using the provided ```docker-compose.yml``` in this repository:
```docker-compose up -d```

### Inject environment variables:
```docker run -d -p 8080:8080 -e JAVA_OPTS=-Xms256m -Xmx512m spring-boot-image```

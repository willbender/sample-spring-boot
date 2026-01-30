# Sample Spring Boot Application

A simple Spring Boot application with a REST API endpoint and JUnit tests.

## Requirements

- Java 17
- Maven 3.6+

## Build and Test

To build and test the application:

```bash
mvn clean verify
```

## Run the Application

```bash
mvn spring-boot:run
```

The application will start on port 8080.

## Test the API

Once running, you can test the Hello World endpoint:

```bash
curl http://localhost:8080/api/hello
```

Expected response: `Hello World!`

## Jenkins Pipeline

The project includes a Jenkinsfile that defines a Docker-based CI/CD pipeline using Maven 3.9.5 with Java 17.

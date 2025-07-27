# Vantix AI Education Platform Backend

A simple Spring Boot MVC application that serves as the backend for the Vantix AI Education Platform.

## Features

- Simple REST API with landing page endpoint
- Health check endpoint for monitoring
- Containerized with Docker
- Multi-stage Docker build for optimized image size
- Non-root user in container for security

## Endpoints

- `GET /` - Returns welcome message: "this is vantix AI education platform"
- `GET /health` - Health check endpoint
- `GET /actuator/health` - Spring Boot actuator health endpoint

## Prerequisites

- Java 17 or higher
- Maven 3.6 or higher
- Docker (for containerization)

## Running Locally

### With Maven

```bash
mvn spring-boot:run
```

### With Java

```bash
mvn clean package
java -jar target/vantix-ai-education-1.0.0.jar
```

The application will start on `http://localhost:8080`

## Running with Docker

### Build and run with Docker commands

```bash
# Build the Docker image
docker build -t vantix-ai-education .

# Run the container
docker run -p 8080:8080 vantix-ai-education
```

### Using Docker Compose (Recommended)

```bash
# Build and run with docker-compose
docker-compose up --build

# Run in detached mode
docker-compose up -d --build

# Stop the service
docker-compose down
```

## Testing the Application

Once the application is running, you can test it:

```bash
# Test the main endpoint
curl http://localhost:8080/

# Test the health endpoint
curl http://localhost:8080/health

# Test the actuator health endpoint
curl http://localhost:8080/actuator/health
```

Expected response from the main endpoint:
```json
{
  "message": "this is vantix AI education platform",
  "status": "active"
}
```

## Configuration

The application uses the following default configuration:
- Port: 8080
- Context path: /
- Logging level: INFO for application, WARN for Spring

Configuration can be modified in `src/main/resources/application.properties`

## Docker Image Details

- Base image: Eclipse Temurin 17 JRE Alpine
- Non-root user: spring (UID 1001)
- Exposed port: 8080
- Health check: Enabled with 30s interval
- Multi-stage build for smaller image size 
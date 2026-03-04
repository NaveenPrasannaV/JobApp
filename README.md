# Client App — JobApp


# JobApp – REST API Gateway

JobApp is a **Spring Boot REST API Gateway** that exposes Job Portal APIs to external clients.  
Instead of directly interacting with the database, this application communicates with a backend **gRPC microservice**.

The project demonstrates a **REST → gRPC Gateway architecture**, where external clients interact with REST APIs while internal services communicate using **gRPC and Protocol Buffers**.


## Architecture

Client (Postman / Web / Mobile)
│
▼
REST API Gateway (JobApp)
Spring Boot + REST
Port: **8080**
│
▼
gRPC Client
│
▼
job-grpc-service (gRPC Microservice)
Port: **9091**
│
▼
PostgreSQL Database

## Features

- REST API Gateway
- Integration with gRPC microservice
- JSON → Protobuf request conversion
- CRUD operations for Job Posts
- Job search functionality
- Microservice communication using HTTP/2

---

## Tech Stack

- Java
- Spring Boot
- gRPC Client
- Protocol Buffers
- Maven
- Lombok

---

## REST API Endpoints

### Get All Jobs
```http
GET /jobs
````

### Get Job By ID

```http
GET /job/{id}
```

### Add Job

```http
POST /job
```

### Update Job

```http
PUT /job
```

### Delete Job

```http
DELETE /job/{id}
```

### Search Jobs

```http
GET /jobs/search/{keyword}
```

---

## Example Request

### Add Job

```json
{
  "postId": 6,
  "postProfile": "DevOps Engineer",
  "postDesc": "AWS Kubernetes",
  "reqExperience": 4,
  "postTechStack": ["AWS", "Docker", "Kubernetes"]
}
```

---

## How It Works

1. Client sends REST request
2. REST Controller receives request
3. Controller calls gRPC Client
4. gRPC Client sends Protobuf request to microservice
5. gRPC server processes request and queries database
6. Response is returned and converted back to JSON

---

## Run the Application

```bash
mvn spring-boot:run
```

Application runs on:

```
http://localhost:8080
```

## Learning Outcome

This project demonstrates how to implement a **REST API Gateway that communicates with backend microservices using gRPC**, a common architecture used in modern distributed systems.

---

If you want, I can also give you a **very polished GitHub version with badges, architecture diagrams, and folder structure** that makes your repo look **like a production microservice project.**

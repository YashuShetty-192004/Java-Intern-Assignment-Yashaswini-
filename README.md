Java Spring Boot Internship Assignment

Candidate Details

Name: Yashaswini KC

Q1: Project Setup & Entity Modelling

Technology Stack

- Java 17
- Spring Boot
- Spring Data JPA
- Maven
- H2 Database
- MySQL
- Lombok
- Validation API

Entities

Client

- id
- name
- industry
- contactEmail
- country
- createdAt

Project

- id
- name
- description
- status
- startDate
- endDate

Sprint

- id
- sprintNumber
- goal
- status
- startDate
- endDate

Task

- id
- title
- description
- priority
- status
- estimatedHours
- actualHours

Engineer

- id
- name
- email
- primaryStack
- experienceYears
- isAvailable

Relationships

- One Client can have many Projects
- One Project can have many Sprints
- One Sprint can have many Tasks
- One Engineer can have many Tasks

Architecture

The application follows a layered architecture:

- Controller Layer
- Service Layer
- Repository Layer
- DTO Layer
- Exception Handling Layer

Business logic is kept in the service layer and not inside controllers.

---

Q2: REST API Design

Client APIs

- POST /api/clients
- GET /api/clients
- GET /api/clients/{id}
- PUT /api/clients/{id}
- DELETE /api/clients/{id}

Project APIs

- POST /api/projects
- GET /api/projects/{id}
- GET /api/projects/{id}/sprints

Sprint APIs

- POST /api/sprints
- GET /api/sprints/{id}
- GET /api/sprints/{id}/summary

Task APIs

- POST /api/sprints/{id}/tasks
- PUT /api/tasks/{id}/status
- PUT /api/tasks/{id}/assign/{engineerId}

Engineer APIs

- GET /api/engineers/{id}/workload
- GET /api/engineers/available

Additional Features

- DTO based request and response handling
- Pagination support
- Sorting support
- Global exception handling
- Soft delete support

---

Q3: What Would Break With 10,000 Projects?

1. No Pagination

Returning all projects at once could cause high memory consumption and slow API responses.

Solution

Use Spring Data Pageable and return paginated results.

---

2. N+1 Query Problem

Improper lazy loading could generate hundreds of database queries.

Solution

Use EntityGraph or Join Fetch queries.

---

3. No Authentication

Anyone could access sensitive endpoints.

Solution

Implement Spring Security and JWT authentication.

---

4. Missing Database Indexes

Queries become slower as data grows.

Solution

Create indexes on:

- client_id
- project_id
- status

---

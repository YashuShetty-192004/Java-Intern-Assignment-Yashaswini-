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
Q4: How To Run Locally

Prerequisites

- Java 17
- Maven 3.8+

Run Application

mvn spring-boot:run

Application URL

http://localhost:8080

H2 Console

http://localhost:8080/h2-console

JDBC URL

jdbc:h2:mem:tekraviodb

Username

sa

Password

password

---

Q5: Resources Used

- Official Spring Boot Documentation
- Spring Data JPA Documentation
- Baeldung Tutorials
- Stack Overflow Discussions
- Tekravio Assignment Instructions

All implementation decisions were completed by me. External resources were used for learning, syntax reference and best practices.

---

Validation & Exception Handling

Validation

- @NotNull
- @NotBlank
- @Email
- @Size

Custom Exceptions

- ResourceNotFoundException
- InvalidStatusTransitionException
- EngineerNotAvailableException

Business Rules

Engineer Availability

An engineer marked unavailable cannot be assigned to a task.

Task Status Flow

TODO → IN_PROGRESS → REVIEW → DONE

Backward transitions are rejected.

---

Sprint Intelligence APIs

Sprint Summary API

GET /api/sprints/{id}/summary

Returns:

- Total tasks
- Completed percentage
- Average completion time
- Tasks by priority
- Overdue task count

Engineer Workload API

GET /api/engineers/{id}/workload

Returns:

- Active tasks
- Tasks by status
- Estimated hours
- Actual hours

Project Health API

GET /api/projects/{id}/health

Health Score Formula:

(70% × Sprint Completion Rate) + (30% × Overdue Task Factor)

Available Engineers API

GET /api/engineers/available?stack=JAVA

Returns engineers who:

- Are available
- Match requested technology stack
- Have fewer than three active tasks

---

Testing

Unit Testing

- JUnit 5
- Mockito

Integration Testing

- SpringBootTest
- MockMvc

Coverage Goal

Minimum 60% service layer coverage.

---

Future Improvements

If given one additional week, I would:

1. Implement JWT Authentication
2. Add Redis Caching
3. Increase Test Coverage
4. Dockerize the Application
5. Configure CI/CD using GitHub Actions

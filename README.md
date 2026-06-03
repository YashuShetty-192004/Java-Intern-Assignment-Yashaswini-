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

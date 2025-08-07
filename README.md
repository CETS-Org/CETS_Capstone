# English Center Management System

This project is a comprehensive system designed to digitize, automate, and centrally manage class enrollment and student tracking for an English language center. It replaces manual processes and fragmented data with an integrated, modern technical solution.

The system's core objective is to enhance operational efficiency and deliver a seamless, transparent user experience on a secure, scalable, and resilient platform built with modern architectural patterns.

## Key Features

*   **Student & Admin Portal:** A secure portal for students to browse courses, manage their profiles, and enroll in classes. Administrators have a dashboard to manage courses, students, and view reports.
*   **Automated Enrollment:** A fully automated, asynchronous enrollment process.
*   **Centralized Tracking:** A unified view of student progress, class schedules, and enrollment data.
*   **Course Catalog Management:** Full CRUD functionality for managing the center's course offerings.

## Technical Architecture

This project is built using a **Hybrid Microservice Architecture** (also known as the Strangler Fig Pattern), combining the development speed of a monolith with the scalability and resilience of microservices for critical business functions.

### Core Components:

*   **Frontend (`ReactJS`):** A modern, single-page application providing a rich user interface.
*   **API Gateway (`Ocelot`):** A single, unified entry point for the frontend, routing requests to the appropriate backend service and handling cross-cutting concerns.
*   **The Monolith (`CEST.API.Web`):** An ASP.NET Core application responsible for stable, core functionalities:
    *   **Identity Management** (Authentication & Authorization using ASP.NET Core Identity)
    *   **Course Catalog Management**
    *   **Student/Class Tracking & Reporting**
*   **The AI Microservice (`CEST.AI`):** A dedicated, independently scalable ASP.NET Core service that handles the most complex and critical business process:
    *   **Saga Pattern:** Implements the Choreography Saga pattern to manage distributed transactions across services (e.g., reserving a class spot and processing payment).
    *   **Transactional Outbox:** Ensures reliable, at-least-once event publishing, even in the event of a system crash.


### Technology Stack & Design Patterns

| Category                 | Technology / Pattern                                                                         | Purpose                                                                                |
| ------------------------ | -------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| **Frontend**             | `ReactJS`, `TypeScript`                                                                      | Building a modern, type-safe, and interactive user interface.                          |
| **Backend**              | `ASP.NET Core 8`, `C#`                                                                       | High-performance, cross-platform framework for building web APIs and services.         |
| **Architecture**         | **Hybrid Microservice Architecture**, **API Gateway**, **CQRS** (implied)                        | Scalability for critical parts, simplicity for others. Single entry point for clients. |
| **Inter-Service Comm.**    | `RabbitMQ` (Asynchronous), `gRPC` (Synchronous - Optional for internal calls)                | Decoupling services, resilience, and high-performance internal communication.          |
| **Messaging Framework**  | `MassTransit`                                                                                | Simplifies messaging, provides robust error handling, retries, and the Outbox pattern. |
| **Data Persistence**     | **Polyglot Persistence**: `SQL Server` (for Monolith) & `MongoDB` (for Microservice - Optional) | Using the right database for the right job (relational vs. document).                  |
| **Data Access**          | `Entity Framework Core`, **Repository Pattern**                                              | ORM for SQL, abstracting data access for testability and maintainability.              |
| **Containerization**     | `Docker`, `Docker Compose`                                                                   | Ensuring consistent development environments and simplifying deployment.                |
| **Distributed Patterns** | **Saga Pattern**, **Transactional Outbox**                                                   | Ensuring data consistency across services and reliable event publishing.               |

## Getting Started

### Prerequisites

*   .NET 8 SDK
*   Docker Desktop
*   Node.js 18+

### Running the System

1.  **Start the Backend Infrastructure & Services:**
    From the root of the backend repository, run Docker Compose. This will start the databases, message broker, and all backend services.
    ```bash
    docker compose up -d
    ```
    Note: If need to remove docker run this:
    ```bash
    docker compose down -v
    ```
    The API Gateway will be available at `http://localhost:8000`.

3.  **Start the Frontend:**
    Navigate to the frontend repository and start the React development server.
    ```bash
    cd ../CETS.FE-StudentTeacher
    npm install
    npm start
    ```
    The application will be available at `http://localhost:3000`.

---

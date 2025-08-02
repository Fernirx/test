**LMS Spring** is a robust, modular RESTful API for university academic management, built with Spring Boot. It provides a solid foundation for managing courses, students, grades, roles, and other operations, ready for integration with UIs or other services.

---

## 🔖 Mục lục
- [Key Features](#key-features)
- [Technologies](#*-technologies)
- [Prerequisites](#prerequisites)
- [Installation & Setup](#installation--setup)
- [Project Structure](#project-structure)
- [Configuration](#configuration)
- [API Documentation](#api-documentation)
- [Security & Health](#security--health)

---

## 🎯Key Features

* **Multi-module design**: Separate core, services, and web layers to ensure a clear separation of concerns and improved maintainability.
* **Profile-based configuration**: Supports `application-{profile}.yaml` patterns for flexible and environment-specific settings (e.g., development, production).
* **Security & validation**: Implements robust security using Spring Security and ensures data integrity with Bean Validation.
* **OpenAPI/Swagger**: Provides auto-generated API documentation and a user-friendly interface for easy API exploration and testing.
* **Actuator & health checks**: Includes built-in monitoring endpoints to check the application's health and gather key metrics.
* **Lombok & MapStruct**: Reduces boilerplate code (e.g., getters, setters) and simplifies object-to-object mapping, respectively, to enhance developer productivity.

---

## ⚙️ Technologies

* **Backend**: Spring Boot 3.5.4
* **Database**: MySQL 8.x, Spring Data JPA
* **API Documentation**: SpringDoc OpenAPI / Swagger UI
* **Security**: Spring Security
* **Utilities**: Lombok, MapStruct
* **Build Tool**: Maven

---

## 🚀 Prerequisites

To build and run this project, you will need the following tools and environments:

* **Java**: Version 21 or newer.
* **Maven**: Version 3.8 or newer.
* **Git**: To clone the repository.
* **Database**: MySQL 8.x (or any other JDBC-compliant database).
* **IDE**: An Integrated Development Environment like IntelliJ IDEA, VS Code, or Eclipse.
* **API Client**: A tool like Postman or Insomnia for testing the API endpoints.

---

## 🛠️ Installation & Setup

1. **Clone repository**

   ```bash
   git clone https://github.com/Fernirx/lms-spring.git
   cd lms-spring
   ```

2. **Create profile config**

   ```bash
   cd application/src/main/resources
   cp application-local.example.yaml application-local.yaml
   ```

   * Edit `application-local.yaml` with your local DB credentials, ports, and any overrides.

3. **Activate your profile**

   * **Option A:** add to `application.yaml`

     ```yaml
     spring:
       profiles:
         active: local
     ```
   * **Option B:** pass as JVM argument

     ```bash
     ./mvnw spring-boot:run -pl application \
       -Dspring-boot.run.arguments="--spring.profiles.active=local"
     ```

4. **Build & run**

   * **With Maven Wrapper**

     ```bash
     ./mvnw clean install
     ./mvnw spring-boot:run -pl application
     ```
   * **Or native Maven**

     ```bash
     mvn clean install
     mvn spring-boot:run -pl application
     ```

---

## 📁 Project Structure

```
lms-system
├── lms-common          # Shared utilities & DTOs
├── lms-core            # Configurations & infrastructure
├── lms-auth            # Authentication & authorization
├── lms-user            # User management
├── lms-academic        # Academic structure management
├── lms-personnel       # Personnel management
├── lms-course          # Course management
├── lms-scheduling      # Scheduling management
├── lms-registration    # Registration management
├── lms-finance         # Finance management
├── lms-communication   # Notice & messaging
├── lms-gradebook       # Gradebook & grades
├── lms-report          # Reporting & analytics
├── lms-gateway         # API gateway
└── lms-admin           # Admin & system management
```

---

## ⚙️ Configuration

* **application.yaml**: common defaults, profile activation
* **application-{profile}.yaml**: overrides per environment (`local`, `server`, `prod`, etc.)
* **application-\*.example.yaml**: template files

> **Tip:** use `${ENV_VAR:default}` placeholders for secrets and set real values via environment variables or CI.

---

## 💬 API Documentation

* Swagger UI: `http://localhost:{port}/swagger`
* OpenAPI JSON: `http://localhost:{port}/api-docs`
* (customize in `application-{profile}.yaml`)
---

## 🔒 Security & Health

* Actuator endpoints:

   * `/actuator/health`
   * `/actuator/metrics`
   * (customize in `application-{profile}.yaml`)
* Configure roles and JWT in `security.yaml` (or your own profile files)

---

**Happy coding!**

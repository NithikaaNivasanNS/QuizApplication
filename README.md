# QuizApplication

# 🧠 Dynamic Quiz Application API

A high-performance **RESTful API** built with Spring Boot to power a dynamic quiz application. This backend handles all core logic, including question management, randomized quiz generation by category, and calculating user scores accurately.

---

### **Badges**

| Status | Source Code | Backend Framework | Language | Database | Build Tool |
| :---: | :---: | :---: | :---: | :---: | :---: |
| [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) | [![GitHub Repo](https://img.shields.io/badge/GitHub-Repository-black.svg)](https://github.com/NithikaaNivasanNS/QuizApplication.git) | [![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.3.0-brightgreen.svg)](https://spring.io/projects/spring-boot) | [![Java](https://img.shields.io/badge/Java-17-orange.svg)](https://www.java.com/) | [![MySQL](https://img.shields.io/badge/MySQL-DB-47A248.svg)]() | [![Maven](https://img.shields.io/badge/Build-Maven-C71A36.svg)](https://maven.apache.org/) |

---

### **Table of Contents**

1.  [# About the Project](#1-about-the-project)
2.  [# Key Features](#2-key-features)
3.  [# Architectural Solution](#3-architectural-solution)
4.  [# Technologies Used](#4-technologies-used)
5.  [# Getting Started (Setup)](#5-getting-started-setup)
6.  [# API Endpoints](#6-api-endpoints)

---

# 1. About the Project

This project is a dedicated **backend API service** for a quiz application. It is designed to be consumed by a separate frontend client (e.g., React, Vue, or a mobile app) to create quizzes, deliver questions, and calculate final scores.

The core goal is to provide a reliable, efficient service for high-volume quiz operations, leveraging Spring Boot's robust features.

# 2. Key Features

* **Question Management (CRUD):** Endpoints to add, retrieve all, and filter questions by category.
* **Dynamic Quiz Creation:** Quizzes are created on demand, selecting a specific number of questions randomly from a given category.
* **Secure Scoring:** Logic to accurately calculate the user's score by comparing submitted responses against the correct answers stored in the database.

# 3. Architectural Solution

The project uses a standard **Spring Boot Layered Architecture** with distinct components:

| Layer | Responsibility | Key Component |
| :--- | :--- | :--- |
| **Controller** | Handles REST requests and defines API endpoints (`@RestController`). | `QuestionController.java`, `QuizController.java` |
| **Service** | Implements all business logic for quiz creation and scoring (`@Service`). | `QuestionService.java`, `QuizService.java` |
| **Repository** | Data access layer using Spring Data JPA. Includes a custom implementation for random question fetching. | `QuestionRepository.java`, `QuizRepository.java` |

# 4. Technologies Used

| Technology | Role | Dependency/Version |
| :--- | :--- | :--- |
| **Spring Boot** | Core framework for building the REST API. | `3.3.0` |
| **Java** | Programming language. | `17` |
| **Spring Data JPA** | Data persistence, mapping Java objects to database tables. | `spring-boot-starter-data-jpa` |
| **MySQL** | Relational database for persistent storage. | `mysql-connector-j` |
| **Lombok** | Boilerplate code reduction (`@Data`, `@RequiredArgsConstructor`). | `org.projectlombok:lombok` |

# 5. Getting Started (Setup)

### Prerequisites

* **Java Development Kit (JDK) 17**
* **Apache Maven**
* **MySQL Server** running locally

### Configuration

1.  **Create MySQL Schema:** Ensure a database schema named `quiz_app` exists on your local MySQL server.
    ```sql
    CREATE DATABASE quiz_app;
    ```

2.  **Update `application.properties`:** Edit the database connection settings in `src/main/resources/application.properties` to ensure the correct credentials.

    ```properties
    spring.datasource.url=jdbc:mysql://localhost:3306/quiz_app?useSSL=false
    spring.datasource.username=root
    spring.datasource.password=Nithikaa@2004 # <-- REPLACE THIS with your actual MySQL password
    spring.jpa.hibernate.ddl-auto=update # Auto-creates/updates tables on startup
    ```

### Running the Application

1.  **Clone the Repository (If not already done):**
    ```bash
    git clone [https://github.com/NithikaaNivasanNS/QuizApplication.git](https://github.com/NithikaaNivasanNS/QuizApplication.git)
    cd QuizApplication
    ```

2.  **Start the Server:** Execute the Spring Boot command using the Maven Wrapper:

    ```bash
    # For Linux/macOS
    ./mvnw spring-boot:run

    # For Windows
    .\mvnw.cmd spring-boot:run
    ```
3.  The API will start on the default port (usually 8080).

# 6. API Endpoints

The API base URL is assumed to be `http://localhost:8080`.

| Feature | HTTP Method | Endpoint | Request Body | Description |
| :--- | :--- | :--- | :--- | :--- |
| **Add New Question** | `POST` | `/questions/addQ` | `Question` object | Adds a new question record to the database. |
| **Get All Questions** | `GET` | `/questions/allQuestions` | None | Retrieves all questions stored in the database. |
| **Questions by Category**| `GET` | `/questions/category/{category}` | None | Retrieves questions filtered by the specified category. |
| **Create Quiz** | `POST` | `/quiz/create?category=...&numQ=...&title=...` | None | Dynamically creates a new quiz instance. |
| **Get Quiz Questions** | `GET` | `/quiz/get/{id}` | None | Retrieves the questions for a specific quiz ID, without the answers. |
| **Submit & Score Quiz** | `POST` | `/quiz/submit/{id}` | List of `Response` objects | Calculates the final score for the submitted quiz ID. |

---

<p align="center">
  <br>
  **Ready to integrate with any modern frontend client!**
</p>

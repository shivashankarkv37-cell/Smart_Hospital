# 🏥 Smart Hospital Management System

A full-stack web application designed to simplify hospital operations by managing patients, doctors, departments, appointments, and hospital workflows through a centralized platform.

The application uses **React.js** for the frontend, **Java Spring Boot** for backend REST APIs, and **MySQL** for persistent data storage.

## 🚀 Project Overview

The Smart Hospital Management System aims to digitize hospital management activities and provide a centralized platform for different hospital users.

It follows a frontend-backend architecture where React communicates with Spring Boot REST APIs, and the backend interacts with MySQL using Spring Data JPA and Hibernate.

## ✨ Features

### 1. User Authentication and Authorization

* User registration and login.
* JWT-based authentication.
* Secure password handling.
* Role-Based Access Control (RBAC).
* Protected API endpoints.

### 2. Patient Management

* Patient registration.
* Patient information management.
* Patient profile retrieval.
* Patient-related operations.

### 3. Doctor Management

* Doctor information management.
* Doctor listing.
* Doctor details retrieval.
* Doctor-related operations.

### 4. Department Management

* Hospital department management.
* Department listing.
* Department information retrieval.

### 5. Appointment Management

* Appointment booking.
* Appointment status management.
* Appointment cancellation.
* Appointment tracking.

Appointment statuses:

* BOOKED
* CANCELLED
* CHECKED_IN
* IN_CONSULTATION
* COMPLETED

### 6. Queue Management

* Appointment check-in.
* Patient queue management.
* Queue-related operations.

### 7. Frontend Integration

* Responsive React.js interface.
* REST API integration using Axios.
* Protected frontend routes.
* Authentication token handling.
* API error handling.

## 🛠️ Technology Stack

| Layer             | Technologies               |
| ----------------- | -------------------------- |
| Frontend          | React.js, Vite, JavaScript |
| Backend           | Java, Spring Boot          |
| ORM               | Hibernate, Spring Data JPA |
| Database          | MySQL                      |
| Security          | Spring Security, JWT       |
| API Communication | REST APIs, Axios           |
| Build Tool        | Maven                      |
| API Testing       | Postman                    |
| IDE               | IntelliJ IDEA, VS Code     |
| Version Control   | Git, GitHub                |

## 🏗️ System Architecture

```text
              USER
                |
                v
       REACT FRONTEND
          (Vite)
                |
                | Axios / HTTP
                |
                v
       SPRING BOOT BACKEND
                |
        REST API Controllers
                |
                v
         SERVICE LAYER
                |
                v
        REPOSITORY LAYER
                |
                v
          MYSQL DATABASE
```

### Application Flow

1. The user interacts with the React frontend.
2. React sends HTTP requests to Spring Boot REST APIs using Axios.
3. Spring Security handles authentication and authorization.
4. Controllers receive incoming requests.
5. Service classes handle business logic.
6. Spring Data JPA communicates with MySQL.
7. The backend returns JSON responses to the frontend.

## 📂 Project Structure

```text
smart-hospital-fullstack/
│
├── smart-hospital-frontend/
│   ├── public/
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── services/
│   │   ├── App.jsx
│   │   ├── main.jsx
│   │   └── index.css
│   ├── package.json
│   └── vite.config.js
│
├── smart-hospital-backend/
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/
│   │   │   │   └── com/example/smart_hospital_backend/
│   │   │   │       ├── controller/
│   │   │   │       ├── service/
│   │   │   │       ├── repository/
│   │   │   │       ├── entity/
│   │   │   │       ├── dto/
│   │   │   │       ├── security/
│   │   │   │       └── SmartHospitalBackendApplication.java
│   │   │   │
│   │   │   └── resources/
│   │   │       └── application.properties
│   │   │
│   │   └── test/
│   ├── pom.xml
│   └── mvnw
│
└── README.md
```

*Note: Adjust the folder names and package structure to match your actual repository.*

## ⚙️ Prerequisites

Install the following before running the application:

* Java JDK 21
* Node.js and npm
* MySQL Server
* Maven
* IntelliJ IDEA or VS Code
* Git

## 💻 Installation and Setup

### Step 1: Clone the Repository

```bash
git clone YOUR_GITHUB_REPOSITORY_URL
```

Navigate into the project:

```bash
cd smart-hospital-fullstack
```

### Step 2: Configure MySQL Database

Open MySQL and execute:

```sql
CREATE DATABASE smart_hospital;
```

### Step 3: Configure Backend

Navigate to the backend directory:

```bash
cd smart-hospital-backend
```

Configure your database credentials and application settings.

Create an `application.properties` file or configure the environment variables.

Example:

```properties
spring.application.name=smart-hospital-backend

server.port=8080

spring.datasource.url=${DB_URL:jdbc:mysql://localhost:3306/smart_hospital}
spring.datasource.username=${DB_USERNAME:root}
spring.datasource.password=${DB_PASSWORD}

spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true

app.jwt.secret=${JWT_SECRET}
```

Configure the following environment variables:

| Variable        | Description                       |
| --------------- | --------------------------------- |
| DB_URL          | MySQL database connection URL     |
| DB_USERNAME     | MySQL username                    |
| DB_PASSWORD     | MySQL password                    |
| JWT_SECRET      | Base64-encoded JWT signing secret |
| FRONTEND_ORIGIN | Frontend application origin       |

**Important:** Never commit actual database passwords, JWT secrets, or other sensitive credentials to GitHub.

### Step 4: Run Backend

Using Maven:

```bash
mvn spring-boot:run
```

Or run the main application class:

```text
SmartHospitalBackendApplication.java
```

Backend server:

```text
http://localhost:8080
```

Health Check API:

```http
GET http://localhost:8080/api/health
```

Expected response:

```text
Smart Hospital Backend is running!
```

### Step 5: Run Frontend

Open another terminal:

```bash
cd smart-hospital-frontend
```

Install dependencies:

```bash
npm install
```

Create a `.env` file:

```env
VITE_API_BASE_URL=http://localhost:8080/api
```

Start the frontend:

```bash
npm run dev
```

Frontend application:

```text
http://localhost:5173
```

## 🔐 Security

The application uses Spring Security to protect backend resources.

Security-related functionality includes:

* JWT-based authentication.
* Password encryption.
* Role-Based Access Control.
* Protected REST API endpoints.
* Authorization checks.
* CORS configuration.

### User Roles

| Role         | Responsibility                     |
| ------------ | ---------------------------------- |
| ADMIN        | Administrative operations          |
| DOCTOR       | Doctor-related operations          |
| RECEPTIONIST | Patient and appointment operations |
| PATIENT      | Patient-related operations         |

Actual permissions depend on the security configuration implemented in the application.

## 🔗 API Endpoints

The backend exposes REST APIs for different hospital operations.

| Module               | HTTP Method | Endpoint           |
| -------------------- | ----------- | ------------------ |
| Health               | GET         | `/api/health`      |
| Authentication       | POST        | `/api/auth/login`  |
| Patient Registration | POST        | `/api/patients`    |
| Doctors              | GET         | `/api/doctors`     |
| Departments          | GET         | `/api/departments` |

### Appointment Management

Appointment operations include booking, cancellation, check-in, and status management.

Refer to the backend controllers for the exact endpoint paths and request formats.

*The endpoint list above is a starting reference. Verify every route against your actual controller mappings before publishing.*

## 🧪 API Testing

REST APIs can be tested using Postman.

Testing includes:

* User registration.
* User login.
* JWT authentication.
* Patient management.
* Doctor management.
* Department management.
* Appointment management.
* Authorization and access control.

For protected endpoints, include the JWT token in the request header:

```http
Authorization: Bearer YOUR_ACCESS_TOKEN
```

## 🔄 Development Workflow

The project follows a layered backend architecture:

**Controller Layer**

* Handles HTTP requests and responses.

**Service Layer**

* Contains business logic.

**Repository Layer**

* Communicates with the database through Spring Data JPA.

**Entity Layer**

* Represents database entities.

**DTO Layer**

* Transfers data between frontend and backend.

**Security Layer**

* Handles JWT authentication and authorization.

## 🚀 Future Enhancements

Potential improvements include:

* Online payment integration.
* Email and SMS notifications.
* Medical report management.
* Advanced analytics dashboard.
* Docker containerization.
* CI/CD pipeline.
* Cloud deployment.
* Redis caching.
* Apache Kafka for asynchronous event processing.

## 🎯 Learning Outcomes

Through this project, the following concepts are explored:

* Full-stack application development.
* REST API development using Spring Boot.
* React frontend integration.
* MySQL database integration.
* Hibernate and Spring Data JPA.
* JWT authentication.
* Role-Based Access Control.
* Layered architecture.
* Frontend-backend communication.
* Git and GitHub version control.

## 👨‍💻 Author

**Shiva Shankar KV**

Aspiring Java Backend / Full-Stack Developer

* GitHub: https://github.com/shivashankarkv37-cell
* LinkedIn: https://linkedin.com/in/shivashankar-kv-

## 📄 License

This project is developed for educational and learning purposes.

You can add an MIT License if you intend to distribute the project under that license.

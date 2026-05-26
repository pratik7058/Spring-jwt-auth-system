# Spring Boot JWT Authentication & Role-Based Authorization

## Overview
This project is a **Spring Boot** application implementing **JWT-based authentication** and **role-based authorization** using **Spring Security**. It provides secure user registration, login, and role management, ensuring that API endpoints are protected based on user roles.

## Features
✅ User registration & login with encrypted passwords
✅ JWT authentication for securing API endpoints
✅ Role-based access control (RBAC) with `ROLE_USER`, `ROLE_ADMIN`, etc.
✅ Secure password hashing with **BCrypt**
✅ RESTful API endpoints for user management
✅ Uses **Spring Security**, **Spring Boot**, **Spring Data JPA**, and **H2/MySQL**

---

## Technologies Used
- **Java 17**
- **Spring Boot 3**
- **Spring Security**
- **JWT (JSON Web Token)**
- **Spring Data JPA (Hibernate)**
- **H2 / MySQL (Configurable)**
- **Lombok**
- **Maven**

---

## Setup & Installation

### Prerequisites
- Java 17+
- Maven
- Postman or any API testing tool

### Steps to Run
1. **Clone the Repository**
   ```sh
   git clone https://github.com/your-username/your-repo-name.git
   cd your-repo-name
   ```
2. **Configure Database & JWT Secret in `application.properties`**
   ```properties
   spring.datasource.url=jdbc:mysql://localhost:3306/yourdb
   spring.datasource.username=root
   spring.datasource.password=yourpassword
   jwt.secret=your_secret_key
   ```
3. **Run the Application**
   ```sh
   mvn spring-boot:run
   ```
4. **Access API at** `http://localhost:8080`

---

## API Endpoints

### **Authentication APIs** (`/api/auth`)
| Method | Endpoint       | Description |
|--------|---------------|-------------|
| **POST**   | `/signup`      | Register a new user |
| **POST**   | `/login`       | Authenticate user & get JWT token |

#### **Register User** (`POST /api/auth/signup`)
**Request Body:**
```json
{
  "username": "john_doe",
  "password": "securePassword123",
  "email": "john@example.com",
  "roles": ["ROLE_ADMIN"]
}
```
**Response:**
```json
{
  "id": 1,
  "username": "john_doe",
  "email": "john@example.com",
  "role": "ROLE_ADMIN"
}
```

#### **Login User** (`POST /api/auth/login`)
**Request Body:**
```json
{
  "username": "john_doe",
  "password": "securePassword123"
}
```
**Response:**
```json
{
  "accessToken": "jwt_token_here"
}
```

---

### **User Management APIs** (`/api/users`)
| Method | Endpoint       | Role Required | Description |
|--------|---------------|---------------|-------------|
| **GET**    | `/`           | `ADMIN`       | Get all users |
| **GET**    | `/{id}`       | `USER`/`ADMIN` | Get user by ID |
| **PUT**    | `/update/{id}` | `ADMIN`       | Update user details |
| **GET**    | `/delete/{id}` | `ADMIN`       | Delete user by ID |

#### **Get All Users** (`GET /api/users`)
**Headers:**
```
Authorization: Bearer <jwt_token>
```
**Response:**
```json
[
  {
    "id": 1,
    "username": "john_doe",
    "email": "john@example.com",
    "role": "ROLE_ADMIN"
  }
]
```

#### **Get User by ID** (`GET /api/users/{id}`)
**Response:**
```json
{
  "id": 1,
  "username": "john_doe",
  "email": "john@example.com",
  "role": "ROLE_ADMIN"
}
```

#### **Update User** (`PUT /api/users/update/{id}`)
**Request Body:**
```json
{
  "username": "new_username",
  "email": "new_email@example.com",
  "roles": ["ROLE_USER"]
}
```

#### **Delete User** (`GET /api/users/delete/{id}`)
**Response:**
```json
{
  "message": "User deleted successfully"
}
```

---

## Authentication & Role Access
- `ADMIN` can access all user-related endpoints.
- `USER` can only access their own profile.
- Every request to protected endpoints **must include** a `Bearer` token in the `Authorization` header.

---

## Contributing
Feel free to open issues and pull requests to improve the project.

---

## Contact
@gmailFor queries, contact 
Gmail: chavan.pratik7058@gmail.com
Linkedin: www.linkedin.com/in/pratik-chavan-21x
GitHub: https://github.com/pratik7058


# Employee Management REST API

A RESTful API built with Spring Boot for managing employee information. This API supports CRUD operations and implements search functionality using three different approaches: JPA Specifications, HQL (Hibernate Query Language), and Native SQL queries.

## Features

- Full CRUD operations for employee records
- Multiple search implementations (JPA Specifications, HQL, Native SQL)
- Input validation for required fields
- Comprehensive error handling with meaningful HTTP status codes
- Unit and integration tests using Mockito and JUnit
- H2 in-memory database for development and testing

## Technology Stack

- **Spring Boot 3.2.0**
- **Spring Data JPA**
- **H2 Database** (in-memory)
- **Lombok** (for reducing boilerplate code)
- **JUnit 5** and **Mockito** (for testing)
- **Java 17**

## API Endpoints

### 1. Fetch Employee Details by Email

#### Using JPA Specifications
```
GET /api/employees/email/{email}/specifications
```

#### Using HQL
```
GET /api/employees/email/{email}/hql
```

#### Using Native SQL
```
GET /api/employees/email/{email}/native
```

### 2. Fetch Employee Details by Name

#### Using JPA Specifications
```
GET /api/employees/name/{name}/specifications
```

#### Using HQL
```
GET /api/employees/name/{name}/hql
```

#### Using Native SQL
```
GET /api/employees/name/{name}/native
```

### 3. Create Employee (Name and Email) - Required

```
POST /api/employees
Content-Type: application/json


### 4. Create Employee (Name, Email, and Phone) - Required

```
POST /api/employees
Content-Type: application/json


### 5. Update Employee Details (Last Name, Phone, and Address)

```
PUT /api/employees/{email}
Content-Type: application/json

### 6. Update Employee Phone Only

```
PATCH /api/employees/{email}/phone
Content-Type: application/json

### 7. Delete Employee by Email

```
DELETE /api/employees/{email}
```

### Bonus: Get All Employees

```
GET /api/employees
```


## Running the Application

### Prerequisites
- Java 17 or higher
- Maven 3.6+

### Build and Run
```bash
cd backend-spring
mvn clean install
mvn spring-boot:run
```

The application will start on `http://localhost:8080`

### Access H2 Console
The H2 database console is available at:
```
http://localhost:8080/h2-console
```

**Connection Details:**
- JDBC URL: `jdbc:h2:mem:employeedb`
- Username: `sa`
- Password: (empty)

## Running Tests

### Run All Tests
```bash
mvn test
```

### Run Unit Tests Only
```bash
mvn test -Dtest=EmployeeServiceTest,EmployeeControllerTest
```

### Run Integration Tests Only
```bash
mvn test -Dtest=EmployeeIntegrationTest
```

## Project Structure

```
backend-spring/
├── src/
│   ├── main/
│   │   ├── java/com/arqonz/employee/
│   │   │   ├── controller/          # REST controllers
│   │   │   ├── dto/                 # Data Transfer Objects
│   │   │   ├── exception/           # Exception handlers
│   │   │   ├── model/               # Entity models
│   │   │   ├── repository/          # Data access layer
│   │   │   └── service/             # Business logic
│   │   └── resources/
│   │       └── application.properties
│   └── test/
│       ├── java/com/arqonz/employee/
│       │   ├── controller/          # Controller unit tests
│       │   ├── integration/         # Integration tests
│       │   └── service/             # Service unit tests
│       └── resources/
│           └── application-test.properties
└── pom.xml
```

## Search Implementation Approaches

The API implements three different approaches for searching employees:

### 1. JPA Specifications
- Dynamic query building using Spring Data JPA Specifications
- Type-safe and flexible
- Endpoints: `/specifications`

### 2. HQL (Hibernate Query Language)
- Object-oriented query language
- Database-agnostic
- Endpoints: `/hql`

### 3. Native SQL Queries
- Raw SQL queries for direct database interaction
- Database-specific optimizations possible
- Endpoints: `/native`

## Validation Rules

- **Name**: Required, cannot be blank
- **Email**: Required, must be a valid email format, must be unique
- **Phone**: Optional
- **Last Name**: Optional
- **Address**: Optional

## Testing

The project includes comprehensive test coverage:

- **Unit Tests**: Test individual components in isolation using Mockito
- **Integration Tests**: Test the full application stack with real database interactions

Test files:
- `EmployeeServiceTest.java` - Service layer unit tests
- `EmployeeControllerTest.java` - Controller layer unit tests
- `EmployeeIntegrationTest.java` - Full integration tests

## License

This project is part of an assessment/assignment.


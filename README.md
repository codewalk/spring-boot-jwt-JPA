# Spring Boot Security + JWT + MySQL Example

This tutorial demonstrates implementing Spring Boot Security with JWT authentication and MySQL for user storage.

## Overview
In a previous tutorial, we implemented Spring Boot + JWT Authentication using hard-coded user values. In this tutorial, we'll enhance it by implementing MySQL JPA for storing and fetching user credentials.

## Steps:

### 1. Dependencies:
Include the required dependencies in your `pom.xml`:

```xml
<!-- Spring Boot Starter Web -->
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
</dependency>

<!-- Spring Boot Starter Security -->
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-security</artifactId>
</dependency>

<!-- JSON Web Token (JWT) -->
<dependency>
    <groupId>io.jsonwebtoken</groupId>
    <artifactId>jjwt</artifactId>
    <version>0.9.1</version>
</dependency>

<!-- Spring Data JPA -->
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-data-jpa</artifactId>
</dependency>

<!-- MySQL Connector -->
<dependency>
    <groupId>mysql</groupId>
    <artifactId>mysql-connector-java</artifactId>
</dependency>
```

### 2. Database Configuration:
Configure database properties in application.properties:
```json
jwt.secret=javainuse
spring.datasource.url=jdbc:mysql://localhost/bootdb?createDatabaseIfNotExist=true&autoReconnect=true&useSSL=false
spring.datasource.username=root
spring.datasource.password=root
spring.datasource.platform=mysql
spring.jpa.hibernate.ddl-auto=create-drop
```

### 3. User Entity:
Create an entity class (DAOUser) representing the user and annotate it with JPA annotations.

### 4. UserDTO:
Define a UserDTO class for transferring user details.

### 5. User Repository:
   Create a UserDao interface that extends CrudRepository for database operations.

### 6. Security Configuration:
   Configure security in WebSecurityConfig class extending WebSecurityConfigurerAdapter.
   Allow /register without security.

### 7. User Details Service:
   Implement JwtUserDetailsService implementing UserDetailsService.
   Autowire UserDao and PasswordEncoder.
   Define save method for inserting user details.

### 8. Controller:
   Modify the controller to handle registration (/register) using a POST request.

### 9. Testing:
   Start the Spring Boot application.
   Register a new user using a POST request to /register.
   Authenticate by creating a POST request to /authenticate.

### 10. Database Authentication:
   Modify UserDao interface to add a method findByUsername.
   Fetch user records from the database in loadUserByUsername.
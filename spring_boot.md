# 🚀 Spring Boot Ultimate Cheatsheet

---

## Module 1: Quickstart

### Building the Quickstart App

What it is: Rapidly create a new Spring Boot project skeleton using Spring Initializr.

Why it's important: Standardizes setup, saves time.

Basic usage:  
Go to [start.spring.io](https://start.spring.io/), select Maven/Gradle, Java/Kotlin, dependencies, and download the ZIP.

Key things to remember: Use Java 17+ for modern Spring Boot.

Example: Generate a microservice with web and JPA dependencies.

---

### Quickstart App Explainer

What it is: Understanding the main entry point and config.

Why it's important: Know where your app starts.

Basic usage:

```java
@SpringBootApplication
public class QuickstartApplication {
    public static void main(String[] args) {
        SpringApplication.run(QuickstartApplication.class, args);
    }
}
```

Key things to remember: `@SpringBootApplication` enables auto-config and component scanning.

Example: Run with `mvn spring-boot:run`.

---

## Module 2: Maven (Build Automation)

### What is Maven?

What it is: Build automation and dependency management for Java.

Why it's important: Handles dependencies, builds, tests, packaging.

Basic usage:  
Configure dependencies in `pom.xml`.

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
</dependency>
```

Key things to remember: Convention over configuration.

Example: Add web starter for REST APIs.

---

### Maven Project Structure

What it is: Standard directory layout.

Why it's important: Consistency and automation.

| Directory          | Purpose        |
| ------------------ | -------------- |
| src/main/java      | Source code    |
| src/main/resources | Config, assets |
| src/test/java      | Tests          |
| target             | Build output   |

Example: Place `application.properties` in resources.

---

### Maven Workflow

What it is: Build lifecycle phases.

Why it's important: Automates compile, test, package, deploy.

Basic usage:

```bash
mvn clean
mvn compile
mvn package
mvn install
mvn deploy
```

Key things to remember: Later phases run earlier ones.

Example: `mvn clean package` for a fresh build.

---

### Maven Spring Boot Plugin

What it is: Plugin for packaging and running Spring Boot apps.

Why it's important: Creates executable JARs, runs app.

Basic usage:

```xml
<plugin>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-maven-plugin</artifactId>
</plugin>
```

Example: Run with `mvn spring-boot:run`.

---

## Module 3: Spring Framework & Boot

### Spring Framework vs Spring Boot

What it is: Spring Framework is the core; Boot adds auto-config and rapid setup.

Why it's important: Boot makes Spring easier and faster.

| Feature | Spring        | Boot                         |
| ------- | ------------- | ---------------------------- |
| Core    | IoC, DI       | Embedded server, auto-config |
| Setup   | Manual config | Minimal config               |

Example: Boot auto-configures database if dependency is present.

---

### Spring App Layers

What it is: Standard separation of concerns.

Why it's important: Modularity and testability.

| Layer      | Annotation      |
| ---------- | --------------- |
| Controller | @RestController |
| Service    | @Service        |
| Repository | @Repository     |

Example: Controller → Service → Repository flow.

---

### Modularity

What it is: Organize code into packages/modules.

Why it's important: Maintainability, team collaboration.

Example:  
`com.example.app.web` (controllers)  
`com.example.app.service` (services)  
`com.example.app.data` (repositories)

---

## Module 4: Dependency Injection (DI)

### Inversion of Control (IoC)

What it is: Container manages object creation and wiring.

Why it's important: Decouples components, easier testing.

Example: Spring injects Repository into Service.

---

### Beans

What it is: Objects managed by Spring.

Why it's important: Only beans can be injected.

Basic usage:

```java
@Service
public class MyService { }
```

Example: Annotate with `@Service`, `@Component`, etc.

---

### Component Scanning

What it is: Auto-detect beans in package hierarchy.

Why it's important: No manual config needed.

Example:  
Classes under main app package with `@Service`, `@Repository` are auto-registered.

---

### @SpringBootApplication

What it is: Combines @Configuration, @EnableAutoConfiguration, @ComponentScan.

Why it's important: One annotation to bootstrap everything.

Example: Place on main class.

---

### Autoconfiguration

What it is: Boot configures beans based on dependencies.

Why it's important: Less boilerplate.

Example: Add H2 dependency, Boot configures DataSource.

---

## Module 5: Configuration

### Configuration Files

What it is: Externalize settings in `application.properties` or `application.yml`.

Why it's important: Change config per environment.

Example:  
`server.port=8081` in properties  
or

```yaml
server:
  port: 8081
```

---

### Environment Variables

What it is: Override config via environment.

Why it's important: Secure secrets, runtime config.

Example:  
`export SERVER_PORT=9090` overrides `server.port`.

---

### Configuration Properties

What it is: Map config to Java objects.

Why it's important: Type-safe config.

Basic usage:

```java
@ConfigurationProperties(prefix = "app.security")
public class SecurityProperties {
    private String tokenSecret;
    // getters/setters
}
```

Example: Map `app.security.token-secret` to field.

---

## Module 6: Databases Part 1 - Basics

### Connect to H2

What it is: In-memory database for dev/testing.

Why it's important: Zero setup, fast prototyping.

Basic usage:

```properties
spring.h2.console.enabled=true
spring.datasource.url=jdbc:h2:mem:testdb
```

Example: Access console at `/h2-console`.

---

### Connect to PostgreSQL

What it is: Production-grade database config.

Why it's important: Persistent storage.

Basic usage:

```properties
spring.datasource.url=jdbc:postgresql://localhost:5432/mydb
spring.datasource.username=dbuser
spring.datasource.password=dbpass
```

---

### Initialise DB Schema

What it is: Auto-create tables via `schema.sql`.

Why it's important: Ensures expected structure.

Example:  
Place `schema.sql` in resources.

---

## Module 7: Databases Part 2 - Spring JDBC

### JDBCTemplate Setup

What it is: Simplifies JDBC operations.

Why it's important: Less boilerplate, safer SQL.

Basic usage:

```java
@Repository
public class UserDao {
    @Autowired JdbcTemplate jdbcTemplate;
}
```

---

### DAO Pattern

What it is: Data Access Object separates persistence logic.

Why it's important: Abstraction and testability.

Example:  
`UserDao` interface with CRUD methods.

---

### Implement DAO

What it is: Write SQL using JdbcTemplate.

Basic usage:

```java
public User create(User user) {
    jdbcTemplate.update("INSERT INTO users ...", ...);
}
```

---

### Read One

What it is: Fetch single record.

Basic usage:

```java
public User findById(Long id) {
    return jdbcTemplate.queryForObject(sql, new UserRowMapper(), id);
}
```

---

### Find Many

What it is: Fetch multiple records.

Basic usage:

```java
public List<User> findAll() {
    return jdbcTemplate.query(sql, new UserRowMapper());
}
```

---

### Update/Delete

What it is: Modify or remove records.

Basic usage:

```java
public int update(User user) { ... }
public int delete(Long id) { ... }
```

---

## Module 8: Databases Part 3 - Spring Data JPA

### Spring Data JPA Setup

What it is: Repository abstraction for JPA.

Why it's important: No boilerplate, auto-implemented queries.

Basic usage:

```java
public interface UserRepository extends JpaRepository<User, Long> { }
```

---

### Entities

What it is: Java classes mapped to DB tables.

Basic usage:

```java
@Entity
public class User {
    @Id @GeneratedValue private Long id;
    private String name;
}
```

---

### Hibernate Auto DDL

What it is: Auto-create/update schema.

Basic usage:

```properties
spring.jpa.hibernate.ddl-auto=update
```

---

### CRUD Operations

What it is: Create, Read, Update, Delete via repository.

Basic usage:

```java
userRepository.save(user);
userRepository.findById(id);
userRepository.findAll();
userRepository.deleteById(id);
```

---

### Custom Queries

What it is: Method name-based queries.

Basic usage:

```java
List<User> findByName(String name);
```

---

### HQL

What it is: Hibernate Query Language for custom queries.

Basic usage:

```java
@Query("SELECT u FROM User u WHERE u.email LIKE %?1%")
List<User> searchByEmailPartial(String emailFragment);
```

---

## Module 9: Jackson & JSON

### Jackson

What it is: Default JSON (de)serializer in Spring Boot.

Why it's important: Auto-converts Java objects to JSON and vice versa.

Example:  
`@RestController` returns Java object, client gets JSON.

---

### JSON Property Annotations

What it is: Customize JSON output.

Basic usage:

```java
@JsonProperty("first_name")
private String firstName;

@JsonIgnore
private String password;
```

---

## Module 10: Build a REST API

### REST API Design

What it is: Standard HTTP CRUD endpoints.

| Action | HTTP      | Path           |
| ------ | --------- | -------------- |
| Create | POST      | /resource      |
| Read   | GET       | /resource/{id} |
| Update | PUT/PATCH | /resource/{id} |
| Delete | DELETE    | /resource/{id} |

---

### Example Endpoints

Create:

```java
@PostMapping("/authors")
public Author create(@RequestBody AuthorDto dto) { ... }
```

Read List:

```java
@GetMapping("/authors")
public List<Author> list() { ... }
```

Read One:

```java
@GetMapping("/authors/{id}")
public Author get(@PathVariable Long id) { ... }
```

Update:

```java
@PutMapping("/authors/{id}")
public Author update(@PathVariable Long id, @RequestBody AuthorDto dto) { ... }
```

Delete:

```java
@DeleteMapping("/authors/{id}")
@ResponseStatus(HttpStatus.NO_CONTENT)
public void delete(@PathVariable Long id) { ... }
```

---

### Pagination

What it is: Divide results into pages.

Basic usage:

```java
@GetMapping
public Page<Author> list(Pageable pageable) {
    return authorRepository.findAll(pageable);
}
```

---

## Module 11: Deployment

### Deploy to AWS LightSail

What it is: Package and run app on cloud VPS.

Basic steps:

1. `mvn clean package` to build JAR
2. Upload JAR to server
3. Run: `java -jar app.jar`
4. Open firewall for app port

Key things to remember: Use process manager for reliability.

Example: Host app for public access.

---

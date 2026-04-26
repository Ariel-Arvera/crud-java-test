# AGENTS.md - crud-test

## Project Overview
- **Type**: Spring Boot REST API
- **Java Version**: 17
- **Framework**: Spring Boot 4.0.6
- **Build Tool**: Maven
- **Database**: H2 (dev), MySQL (prod)

## Directory Structure
```
src/
  main/java/com/api/crud/
    models/      - JPA entities
    repositories/ - Spring Data JPA repositories
    services/    - Business logic
    controllers/ - REST controllers
  test/java/com/api/crud/ - Integration tests
```

## Build/Lint/Test Commands

### Build
```bash
./mvnw clean install              # Full build
./mvnw clean package              # Package without tests
./mvnw clean compile              # Compile only
```

### Test
```bash
./mvnw test                      # Run all tests
./mvnw test -Dtest=CrudTestApplicationTests  # Run single test class
./mvnw test -Dtest=CrudTestApplicationTests#contextLoads  # Run single method
./mvnw test -Dtest=ClassName#methodName     # Run specific test
```

### Run
```bash
./mvnw spring-boot:run            # Run application
java -jar target/crud-test-0.0.1-SNAPSHOT.jar
```

### Other
```bash
./mvnw dependency:sources         # Download sources
./mvnw dependency:tree          # View dependency tree
```

## Code Style Guidelines

### Package Naming
- Use lowercase: `com.api.crud.models`, `com.api.crud.services`
- Group by feature/type: `controllers`, `repositories`, `services`

### Class Naming
- Models: `UserModel`, `ProductModel`
- Repositories: `IUserRepository` (prefix I for interfaces)
- Services: `UserService`
- Controllers: `UserController`

### Variable Naming
- camelCase: `firstName`, `lastName`, `userRepository`
- Descriptive names: avoid single letters except loops
- Private fields: no prefix (e.g., `id`, `email`)

### Import Organization
1. `java.*`
2. `javax.*`
3. Third-party (`org.springframework`, `jakarta`)
4. Project imports (`com.api.crud.*`)
- No unused imports
- No wildcard imports except for `java.util.*` when needed

### Annotations
- Entity: `@Entity`, `@Table(name = "table_name")`
- JPA: `@Id`, `@GeneratedValue`, `@Column`
- Spring: `@Service`, `@Repository`, `@RestController`, `@Autowired`
- HTTP: `@GetMapping`, `@PostMapping`, `@PutMapping`, `@DeleteMapping`

### Error Handling
- Services: Return `Optional<T>` for nullable results, `Boolean` for operations
- Controllers: Handle null checks, return meaningful error messages
- Use try-catch sparingly; prefer Spring exception handling for production

### REST Conventions
- Base path: `@RequestMapping("/user")`
- GET: List (`/user`), Get by ID (`/user/{id}`)
- POST: Create (`/user`)
- PUT: Update (`/user/{id}`)
- DELETE: Delete (`/user/{id}`)

### Java 17 Conventions
- Use `jakarta.persistence` (not `javax.persistence`)
- Use `@Autowired` on constructor for required dependencies
- Return `Optional<T>` instead of null
- Use diamond operator where type is obvious

### Testing
- Use `@SpringBootTest` for integration tests
- Use `@Test` from `org.junit.jupiter.api.Test`
- Keep tests focused, one assertion per test where practical

## Database Conventions
- Table names: lowercase singular (`user`)
- Column names: lowercase camelCase in Java, snake_case in DB
- Use `@Table(name = "user")` for custom table names

## Common Patterns
- Service layer returns collections as `ArrayList<T>`
- Repository layer extends `JpaRepository<Entity, Long>`
- Use constructor injection where possible: `@Autowired UserService(IUserRepository repo)`
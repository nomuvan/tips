# GitHub Copilot Context

This is the project-specific Copilot context for kabu25.

## Project Description

kabu25 is a Java Maven multi-module project built with Quarkus framework for Japanese stock market data integration and processing. The project follows a modular architecture with shared API libraries for code reusability.

## Guidelines

### Code Organization Patterns
- Use Maven multi-module architecture with clear separation of concerns
- Extract shared API client code into reusable library modules (pattern established with kabu25-kabustation-api)
- Follow package naming convention: `net.kabu25.{module-name}` for services, `net.kabu25.{service}.api` for shared libraries
- Place business logic in service modules, not API library modules

### Technical Standards
- Java 21 with Quarkus 3.22.1 framework
- Use Lombok for POJO generation and code reduction
- Implement REST clients using Quarkus REST Client with JAX-RS annotations
- Use header factories for cross-cutting concerns (authentication, host headers)
- Implement proper Maven dependency management through parent POM

### Development Workflow
- Use feature branches for all development (e.g., feature/issue1)
- Create comprehensive pull requests with detailed descriptions
- Update Memory Bank documentation when making architectural changes
- Ensure all modules build successfully before creating PRs

### Architecture Decisions Learned
- Shared library pattern successful: kabu25-kabustation-api module can be reused across services
- Build order matters: API libraries must be built before dependent service modules
- Package restructuring requires careful import statement updates across all affected files
- Maven dependency direction: service modules depend on API modules (not vice versa)
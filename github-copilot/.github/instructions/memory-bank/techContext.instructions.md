---
applyTo: "**"
---
# Important Note
This file is a part of the Memory Bank. It is essential for understanding the project and its current state. I MUST read this file at the start of EVERY task.
To ensure I have the most up-to-date context, this file should be very flexible and updated frequently.

# Technical Context: kabu25

## Technology Stack
### Core Framework
- **Quarkus 3.22.1**: Primary application framework
  - Supersonic Subatomic Java Framework
  - Native compilation support
  - Dev UI available at http://localhost:8080/q/dev/
  - Hot reload in dev mode

### Language & Runtime
- **Java 21**: Primary development language
- **Maven 3.x**: Build and dependency management
- **Lombok 1.18.36**: Code generation for POJOs

### Dependencies & Libraries
- **Jackson**: JSON processing and serialization
- **Quarkus REST Client**: HTTP client for external API integration
- **JUnit/Jupiter**: Testing framework
- **Quarkus Test**: Quarkus-specific testing utilities

## Development Setup
### Build Configuration
```xml
<maven.compiler.source>21</maven.compiler.source>
<maven.compiler.target>21</maven.compiler.target>
<maven.compiler.release>21</maven.compiler.release>
<project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
```

### Module Structure
```
kabu25-parent/
├── kabu25-kabustation/          # Main KabuStation service
├── kabu25-kabustation-api/      # Shared API client library
└── kabu25-rss-receiver/         # RSS processing service
```

## Technical Constraints
- **Java Version**: Must use Java 21 features and syntax
- **Maven Dependencies**: All modules inherit from kabu25-parent POM
- **Package Structure**: 
  - Services: `net.kabu25.{service-name}`
  - API Library: `net.kabu25.kabustation.api`
- **REST Client**: Use Quarkus REST Client annotations for HTTP integration

## Integration Patterns
### KabuStation API Integration
- Token-based authentication with refresh mechanism
- Header factories for consistent request formatting
- REST client interfaces with JAX-RS annotations
- Message models with Jackson annotations

### Configuration Management
- Quarkus application.properties for environment-specific settings
- Profile-based configuration support
- External configuration for API endpoints and credentials

## Docker Support
- Dockerfile variants provided:
  - `Dockerfile.jvm` - Standard JVM deployment
  - `Dockerfile.native` - Native compilation
  - `Dockerfile.native-micro` - Minimal native image
  - `Dockerfile.legacy-jar` - Traditional JAR deployment

## Development Commands
### Local Development
```bash
./mvnw quarkus:dev          # Run in dev mode with hot reload
./mvnw clean install       # Build all modules
./mvnw package             # Package applications
```

### Testing
```bash
./mvnw test               # Run unit tests
./mvnw quarkus:test       # Run Quarkus continuous testing
```

### Native Build
```bash
./mvnw package -Dnative                                    # Native build
./mvnw package -Dnative -Dquarkus.native.container-build=true # Container-based native build
```

## IDE Support
- **Primary IDE**: VS Code with Java extensions
- **Quarkus Tools**: VS Code Quarkus extension for enhanced development experience
- **Debugging**: Dev mode supports hot code replacement

## External Dependencies
### KabuStation API
- Authentication: Token-based with X-API-KEY header
- Host header: Required for routing requests
- Rate limiting: Must be considered in implementation

### RSS Feeds
- Standard RSS/Atom feed parsing
- Scheduled polling for updates
- Feed validation and error handling

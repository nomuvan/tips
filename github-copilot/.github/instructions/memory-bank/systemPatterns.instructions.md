---
applyTo: "**"
---
# Important Note
This file is a part of the Memory Bank. It is essential for understanding the project and its current state. I MUST read this file at the start of EVERY task.
To ensure I have the most up-to-date context, this file should be very flexible and updated frequently.

# System Patterns: kabu25

## Architecture Overview
The kabu25 system follows a **multi-module Maven architecture** with **shared library pattern** for common functionality.

```
┌─────────────────────────────────────────────────────────┐
│                    kabu25-parent                        │
│                   (Parent POM)                          │
└─────────────────────┬───────────────────────────────────┘
                      │
     ┌────────────────┼────────────────┐
     │                │                │
     ▼                ▼                ▼
┌─────────┐    ┌──────────────┐  ┌─────────────┐
│kabu25-  │    │kabu25-       │  │kabu25-      │
│rss-     │    │kabustation   │  │kabustation- │
│receiver │    │              │  │api          │
└─────────┘    └──────┬───────┘  └─────────────┘
                      │                 ▲
                      └─────────────────┘
                         depends on
```

## Key Design Patterns

### 1. Shared Library Pattern
**Pattern**: Extract common API client code into reusable library
**Implementation**: kabu25-kabustation-api module
**Benefits**: 
- Code reuse across multiple services
- Consistent API integration patterns
- Centralized maintenance of external API clients

### 2. Maven Multi-Module Pattern
**Structure**:
```xml
<packaging>pom</packaging>
<modules>
    <module>kabu25-rss-receiver</module>
    <module>kabu25-kabustation</module>
    <module>kabu25-kabustation-api</module>
</modules>
```

### 3. REST Client Factory Pattern
**Components**:
- `KabuStationRestClient` - Main API interface
- `KabuStationTokenRestClient` - Authentication API interface
- `TokenHeaderFactory` - X-API-KEY header injection
- `HostHeaderFactory` - Host header management

### 4. Token Service Pattern
**Implementation**: `KabuStationTokenService`
- Centralized token management
- Automatic token refresh logic
- Thread-safe token caching

### 5. Message Model Pattern
**Package Structure**: `net.kabu25.kabustation.api.message`
**Components**:
- Request models: `TokenRequest`, `RankingRequest`
- Response models: `TokenResponse`, `RankingResponse`, `WalletResponse`
- Enum models: `ExchangeDivision`, `RankingType`, `Trend`

## Component Relationships

### API Client Layer
```
KabuStationRestClient
├── Uses: TokenHeaderFactory
├── Uses: HostHeaderFactory
└── Returns: Message Models

KabuStationTokenRestClient
├── Uses: No factories (authentication endpoint)
└── Returns: TokenResponse
```

### Service Layer
```
KabuStationTokenService
├── Uses: KabuStationTokenRestClient
├── Manages: Token lifecycle
└── Provides: Token to HeaderFactory
```

### Data Layer
```
Message Models
├── TokenRequest/Response
├── RankingRequest/Response
├── WalletResponse
└── Enum Models (ExchangeDivision, RankingType, Trend)
```

## Package Organization

### Service Modules
```
net.kabu25.{module-name}/
├── scheduler/          # Scheduled tasks
├── provider/          # JAX-RS providers
└── test/             # Integration tests
```

### API Library Module
```
net.kabu25.kabustation.api/
├── client/           # REST client interfaces
├── service/          # Business logic services
├── factory/          # Header and parameter factories
├── provider/         # JAX-RS providers (ParamConverter, etc.)
└── message/          # Data transfer objects
```

## Integration Patterns

### HTTP Client Pattern
- Use Quarkus REST Client with JAX-RS annotations
- Implement header factories for cross-cutting concerns
- Separate authentication and business API clients

### Scheduler Pattern
- Use Quarkus Scheduler for periodic tasks
- Implement in service modules, not API library
- Example: `KabustationOpeningRankingLogScheduler`

### Provider Pattern
- Implement JAX-RS providers for parameter conversion
- Place providers in API library for reusability across services
- Example: `KabuStationQueryParamConverterProvider` in kabu25-kabustation-api
- Automatic detection via @Provider annotation by Quarkus

## Error Handling Patterns
- Use standard HTTP status codes
- Implement retry logic in service layer
- Centralize error responses in message models

## Configuration Patterns
- Use Quarkus `application.properties` for environment-specific configuration
- Implement configuration injection via `@ConfigProperty`
- Support multiple profiles (dev, test, prod)

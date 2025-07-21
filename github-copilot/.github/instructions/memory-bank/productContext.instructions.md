---
applyTo: "**"
---
# Important Note
This file is a part of the Memory Bank. It is essential for understanding the project and its current state. I MUST read this file at the start of EVERY task.
To ensure I have the most up-to-date context, this file should be very flexible and updated frequently.

# Product Context: kabu25

## Why This Project Exists
kabu25 exists to provide a comprehensive platform for Japanese stock market data integration and processing. The project aims to solve the fragmentation problem in stock market data access by creating unified, reusable components.

## Problems It Solves
1. **Data Source Fragmentation**: Multiple stock market data sources (KabuStation API, RSS feeds) require different integration approaches
2. **Code Duplication**: Common API client code was previously duplicated across modules
3. **Scalability Issues**: Monolithic approach made it difficult to add new data sources
4. **Maintenance Overhead**: Tightly coupled code made updates and maintenance difficult

## How It Should Work
### User Experience Goals
- **Developers**: Easy integration of stock market data sources through well-defined APIs
- **Operations**: Simple deployment and scaling of individual services
- **Maintainers**: Clear module boundaries and reusable components

### System Behavior
1. **KabuStation Integration**: 
   - Authenticate with KabuStation API using token-based authentication
   - Fetch ranking data, wallet information, and other market data
   - Process and schedule data retrieval operations

2. **RSS Feed Processing**:
   - Monitor and process RSS feeds for market news and updates
   - Parse and normalize feed data for downstream processing

3. **API Client Reusability**:
   - Shared API client library (kabu25-kabustation-api) for consistent KabuStation integration
   - Common message models and REST client interfaces
   - Header factories for authentication and host management

## Target Architecture
```
┌─────────────────────┐    ┌─────────────────────┐
│  kabu25-kabustation │    │ kabu25-rss-receiver │
│                     │    │                     │
└──────────┬──────────┘    └─────────────────────┘
           │                          
           ▼                          
┌─────────────────────┐               
│kabu25-kabustation-  │               
│       api           │               
│  (Shared Library)   │               
└─────────────────────┘               
```

## Success Metrics
- Clean separation of concerns between modules
- Reusable API components across multiple services
- Successful integration with external data sources
- Maintainable and scalable codebase

## Future Vision
- Support for additional Japanese stock market data sources
- Real-time data processing capabilities
- Advanced analytics and data transformation services
- Web dashboard for data visualization

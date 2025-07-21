---
applyTo: "**"
---
# Important Note
This file is a part of the Memory Bank. It is essential for understanding the project and its current state. I MUST read this file at the start of EVERY task.
To ensure I have the most up-to-date context, this file should be very flexible and updated frequently.

# Active Context: kabu25

## Current Work Focus
**Status**: Recently completed major refactoring - Issue #1 implementation
**Branch**: main (feature/issue1 merged via PR #2)
**Last Major Work**: Extraction of kabu25-kabustation-api module

## Recent Changes

### 2025/07/21 - Issue #1 Implementation Completed
- **Created**: kabu25-kabustation-api Maven subproject
- **Extracted**: All KabuStation API client code from kabu25-kabustation
- **Package Restructure**: 
  - From: `net.kabu25.kabustation.*`
  - To: `net.kabu25.kabustation.api.*`
- **Components Moved**:
  - Client interfaces: `KabuStationRestClient`, `KabuStationTokenRestClient`
  - Services: `KabuStationTokenService`
  - Factories: `TokenHeaderFactory`, `HostHeaderFactory`
  - Messages: All request/response models and enums
  - Providers: `KabuStationQueryParamConverterProvider` (moved to api.provider)

### 2025/07/21 - Provider Package Migration Completed
- **Moved**: `KabuStationQueryParamConverterProvider` from kabu25-kabustation to kabu25-kabustation-api
- **Package Change**: 
  - From: `net.kabu25.kabustation.provider`
  - To: `net.kabu25.kabustation.api.provider`
- **Removed**: provider package directory from kabu25-kabustation module
- **Verified**: All modules compile successfully after provider migration
- **Purpose**: Complete consolidation of API-related components in shared library

### Build & Integration Changes
- **Updated parent POM**: Added kabu25-kabustation-api module
- **Updated kabu25-kabustation POM**: Added dependency to API module
- **Fixed imports**: All affected files updated with new package names
- **Verified builds**: Both modules compile successfully
- **Created PR #2**: "Create kabu25-kabustation-api subproject"

## Current State

### Module Status
✅ **kabu25-parent**: Root POM managing all modules
✅ **kabu25-kabustation-api**: New shared library - COMPLETED
✅ **kabu25-kabustation**: Updated to use API module - COMPLETED  
✅ **kabu25-rss-receiver**: Existing module - STABLE

### Build Status
- All modules compile successfully
- Maven dependency resolution working
- No outstanding compilation errors

### Git Status
- Feature branch: `feature/issue1` - MERGED
- Pull Request: #2 - COMPLETED
- Current branch: main
- Repository: Clean state

## Next Steps
1. **Monitor PR #2**: Await any feedback or approval for the completed implementation
2. **Potential Enhancements**: 
   - Add comprehensive documentation for kabu25-kabustation-api
   - Consider adding integration tests for the API module
   - Evaluate additional modules that could benefit from the shared API library

## Active Decisions & Considerations

### Technical Decisions Made
- **Package naming**: Chose `net.kabu25.kabustation.api` for clear API library identification
- **Module separation**: Complete separation of API client from service logic
- **Dependency direction**: Service modules depend on API module (not vice versa)
- **Build order**: API module built first, then dependent modules

### Design Considerations
- **Reusability**: API module designed for use by multiple service modules
- **Docker exclusion**: As specified in Issue #1, docker processing not included in API module
- **Maven coordinates**: Used consistent versioning (1.0.0-SNAPSHOT) across modules

## Development Context
- **IDE**: VS Code with Java extensions
- **Java Version**: 21
- **Framework**: Quarkus 3.22.1
- **Build Tool**: Maven 3.x
- **OS**: macOS

## Memory Bank Status
### 2025/07/21 - Memory Bank Creation
- **Created**: Complete Memory Bank structure
- **Documented**: Current project state and recent changes
- **Captured**: All architectural decisions and patterns
- **Status**: Up-to-date with latest project state

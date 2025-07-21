---
applyTo: "**"
---
# Important Note
This file is a part of the Memory Bank. It is essential for understanding the project and its current state. I MUST read this file at the start of EVERY task.
To ensure I have the most up-to-date context, this file should be very flexible and updated frequently.

# Project Brief: kabu25

## Project Overview
kabu25 is a Java Maven multi-module project built with Quarkus framework for stock market data processing and analysis. The project is designed as a modular system that can handle various aspects of stock market data integration and processing.

## Core Requirements
- **Language**: Java 21
- **Framework**: Quarkus 3.22.1
- **Build System**: Maven with multi-module architecture
- **Architecture**: Microservices-based with reusable API components

## Project Goals
1. **Data Integration**: Integrate with external stock market data sources (KabuStation API, RSS feeds)
2. **Modular Design**: Create reusable components that can be shared across different services
3. **Scalability**: Design for future expansion with additional data sources and processing modules
4. **API Abstraction**: Extract common API client code into reusable libraries

## Module Structure
- **kabu25-parent**: Root parent POM managing dependencies and build configuration
- **kabu25-kabustation**: Service for KabuStation integration and data processing
- **kabu25-kabustation-api**: Extracted API client library for KabuStation (reusable)
- **kabu25-rss-receiver**: Service for RSS feed processing

## Key Technologies
- Quarkus 3.22.1 (Supersonic Subatomic Java Framework)
- Java 21
- Maven 3.x
- Lombok 1.18.36
- Jackson for JSON processing
- Quarkus REST Client

## Development Workflow
- Feature branch development
- GitHub integration with issues and pull requests
- Maven-based build and dependency management
- Docker containerization support (via Quarkus)

## Repository Information
- **GitHub**: nomuvan/kabu25
- **Main Branch**: main
- **Development**: Feature branches (e.g., feature/issue1)

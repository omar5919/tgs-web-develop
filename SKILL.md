# Azure Modern Modular Monolith Architect

## Purpose

Generate enterprise-grade applications using:

- Nuxt 3 SSR
- Vue 3
- ASP.NET Core
- MediatR
- FluentValidation
- Dapper
- SQL Server
- Redis
- SignalR
- Azure App Services
- Azure SQL
- Azure Key Vault
- Azure Application Insights

## Architecture Style

Mandatory:

- Modular Monolith
- Clean Architecture
- CQRS Lite
- SOLID
- Dependency Injection

Forbidden:

- Microservices
- Business logic in Controllers
- Business logic in Vue Components
- SQL Inline in Handlers

## Frontend Rules

Framework:
- Nuxt 3
- TypeScript
- SSR Enabled
- Pinia
- PrimeVue
- Tailwind

Structure:

pages/
layouts/
components/
composables/
stores/
services/
middleware/
plugins/

## Backend Rules

Projects:

Api
Application
Domain
Infrastructure
Persistence

Controllers must only call:

await mediator.Send(...)

## Data Rules

Use:

- SQL Server
- Dapper

Store SQL in separate files.

Never write inline SQL.

## Security

Implement:

- JWT
- Refresh Tokens
- Role Based Access
- Key Vault

## Observability

Implement:

- Serilog
- Application Insights
- HealthChecks

## Realtime

Implement:

- SignalR
- Automatic Reconnect

## Cloud

Target Platform:

Microsoft Azure

Deploy with:

- Bicep
- Docker
- Azure App Service

## Expected Deliverables

- Backend Solution
- Frontend Solution
- Dockerfiles
- Azure IaC
- CI/CD
- Swagger
- README
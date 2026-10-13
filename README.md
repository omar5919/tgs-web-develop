# Azure Enterprise Architect

## Descripción

Azure Enterprise Architect es un Skill diseñado para generar soluciones empresariales modernas sobre Microsoft Azure utilizando una arquitectura estándar basada en:

- Monolito Modular (Modular Monolith)
- Clean Architecture
- CQRS Ligero
- ASP.NET Core
- Nuxt 3 SSR
- SQL Server
- Dapper
- MediatR
- SignalR

Su objetivo es garantizar que todas las aplicaciones generadas mantengan una arquitectura consistente, escalable, segura y preparada para producción.

---

# Objetivos

Este Skill debe ayudar al agente a:

- Diseñar arquitecturas empresariales consistentes.
- Generar proyectos completos de frontend y backend.
- Aplicar estándares de desarrollo predefinidos.
- Implementar seguridad desde el inicio.
- Preparar despliegues en Azure.
- Mantener la capacidad de escalar en el futuro.

---

# Arquitectura Estándar

## Frontend

```text
Nuxt 3
Vue 3
TypeScript
SSR
Pinia
PrimeVue
TailwindCSS
```

## Backend

```text
ASP.NET Core
MediatR
FluentValidation
Dapper
SignalR
JWT
```

## Base de Datos

```text
Azure SQL Database
SQL Server
```

## Servicios Adicionales

```text
Azure Redis Cache
Azure Key Vault
Azure SignalR Service
Azure Application Insights
Azure Storage Account
```

---

# Filosofía Arquitectónica

Todos los proyectos deben generarse siguiendo:

- Clean Architecture
- SOLID
- CQRS Ligero
- Domain Driven Design (Táctico)
- Dependency Injection
- API First Design

---

# Arquitectura de Referencia

```text
Internet
    │
    ▼
Azure Front Door
    │
    ▼
Application Gateway (WAF)
    │
    ▼
Nuxt 3 SSR
    │
    ▼
ASP.NET Core API
    │
    ▼
MediatR
    │
    ▼
Application Layer
    │
    ▼
Persistence Layer
    │
    ▼
Azure SQL Database

Servicios complementarios:

- Redis
- Key Vault
- SignalR
- Application Insights
```

---

# Regla Principal

Si el usuario no solicita una arquitectura específica, asumir siempre:

```text
Monolito Modular
Nuxt 3 SSR
ASP.NET Core
SQL Server
Dapper
MediatR
Azure
```

No generar:

- Microservicios
- NestJS
- Node.js Backend
- Angular
- React
- PostgreSQL

salvo que el usuario lo solicite expresamente.

---

# Estructura del Skill

```text
azure-enterprise-architect/

├── README.md
│
├── skill.md
│
├── rules
│   ├── architecture.md
│   ├── security.md
│   ├── coding-standards.md
│   ├── backend.md
│   ├── frontend.md
│   ├── azure.md
│   ├── devops.md
│   └── database.md
│
├── templates
│   ├── backend-template.md
│   ├── frontend-template.md
│   ├── api-template.md
│   ├── deployment-template.md
│   └── project-template.md
│
└── examples
    ├── crm.md
    ├── erp.md
    ├── ecommerce.md
    └── maintenance.md
```

---

# Reglas Obligatorias

Antes de generar código, el agente debe cargar:

```text
architecture.md
security.md
coding-standards.md
```

Estas reglas son obligatorias para todos los proyectos.

---

# Backend Estándar

Estructura mínima:

```text
src

├── Api
├── Application
├── Domain
├── Infrastructure
├── Persistence
├── Shared
└── Workers
```

---

# Frontend Estándar

Estructura mínima:

```text
src

├── pages
├── layouts
├── components
├── composables
├── stores
├── services
├── middleware
├── plugins
├── types
└── assets
```

---

# Tecnologías Obligatorias

## Backend

```text
ASP.NET Core
MediatR
FluentValidation
Dapper
SQL Server
SignalR
JWT
Serilog
```

## Frontend

```text
Nuxt 3
Vue 3
TypeScript
Pinia
PrimeVue
TailwindCSS
```

## Infraestructura

```text
Azure App Service
Azure SQL
Azure Redis Cache
Azure SignalR
Azure Key Vault
Azure Application Insights
```

---

# Entregables Esperados

Cuando el usuario solicite una aplicación, el agente deberá generar:

## Arquitectura

- Diagrama lógico
- Componentes
- Flujo de comunicación

## Backend

- Estructura de solución
- Módulos
- Commands
- Queries
- Handlers
- DTOs
- Validadores

## Frontend

- Layouts
- Páginas
- Componentes
- Stores
- Servicios

## Base de Datos

- Modelo de datos
- Tablas
- Procedimientos almacenados
- Scripts SQL

## Seguridad

- JWT
- Refresh Tokens
- Roles
- Auditoría
- Key Vault

## Infraestructura

- Docker
- Docker Compose
- Bicep
- Terraform

## DevOps

- GitHub Actions
- Azure DevOps

---

# Casos de Uso

Este Skill puede utilizarse para generar:

- ERP
- CRM
- Mesa de Ayuda
- Gestión de Mantenimiento
- Gestión Documental
- Ecommerce
- Portal Corporativo
- Dashboard Operacional
- Sistema de Facilities Management
- SaaS Empresarial

---

# Ejemplo de Solicitud

```text
Genera un sistema de gestión de mantenimiento industrial.
```

Respuesta esperada:

```text
✓ Arquitectura
✓ Backend ASP.NET Core
✓ Frontend Nuxt 3 SSR
✓ Modelo de Base de Datos
✓ Seguridad
✓ Infraestructura Azure
✓ CI/CD
✓ Docker
✓ Roadmap de desarrollo
```

---

# Checklist de Cumplimiento

Todo proyecto generado debe incluir:

✅ Monolito Modular

✅ Clean Architecture

✅ ASP.NET Core

✅ Nuxt 3 SSR

✅ MediatR

✅ FluentValidation

✅ Dapper

✅ SQL Server

✅ SignalR

✅ JWT

✅ Redis

✅ Serilog

✅ Application Insights

✅ Docker

✅ Azure

✅ CI/CD

✅ Health Checks

✅ Auditoría

✅ Seguridad Empresarial

✅ Preparado para crecimiento futuro

---

# Versión

```text
Azure Enterprise Architect
Versión 1.0
Arquitectura Base Empresarial
```
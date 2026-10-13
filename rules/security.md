# Estándares de Seguridad

## Objetivo

Definir los lineamientos de seguridad obligatorios para todas las soluciones generadas por este agente.

Estas reglas deben aplicarse siempre, salvo que el usuario indique lo contrario.

---

# Autenticación

## Estándar obligatorio

Implementar:

- JWT Access Token
- Refresh Token

Configuración mínima:

- Access Token: 60 minutos
- Refresh Token: 7 días

Los Refresh Tokens deben almacenarse en base de datos.

No utilizar LocalStorage para almacenar tokens.

Preferir:

- Cookies HTTP Only
- Cookies Secure

---

# Autorización

Utilizar control de acceso basado en roles (RBAC).

Roles mínimos:

- Admin
- Manager
- User

Ejemplos:

Admin
    Acceso total

Manager
    Acceso operativo

User
    Acceso limitado

Implementar:

```csharp
[Authorize]
```

o

```csharp
[Authorize(Roles = "Admin")]
```

Toda autorización debe validarse en el backend.

Nunca confiar en restricciones impuestas únicamente por el frontend.

---

# Contraseñas

Longitud mínima:

12 caracteres

Requisitos:

- Mayúsculas
- Minúsculas
- Números
- Caracteres especiales

No almacenar contraseñas en texto plano.

Utilizar:

- ASP.NET Identity PasswordHasher
- BCrypt

---

# Protección contra SQL Injection

Obligatorio utilizar consultas parametrizadas.

Correcto:

```csharp
SELECT * FROM Users WHERE Id = @Id
```

Incorrecto:

```csharp
SELECT * FROM Users WHERE Id = " + id
```

Toda consulta Dapper debe utilizar parámetros.

---

# Gestión de Secretos

Prohibido almacenar:

- API Keys
- Connection Strings
- Passwords
- Certificados

en:

- Código fuente
- Git
- appsettings.json

Utilizar:

- Azure Key Vault
- Managed Identity

---

# Validaciones

Toda entrada debe validarse mediante:

- FluentValidation

Validar:

- Request Body
- Query String
- Route Parameters
- Archivos

Nunca confiar en validaciones del frontend.

---

# Seguridad API

Habilitar:

- HTTPS obligatorio
- HSTS
- Redirección HTTP → HTTPS

Agregar cabeceras:

- X-Content-Type-Options
- X-Frame-Options
- Content-Security-Policy
- Referrer-Policy

---

# CORS

Restringir orígenes permitidos.

Incorrecto:

```csharp
AllowAnyOrigin()
```

Correcto:

```text
https://portal.empresa.com
https://app.empresa.com
```

---

# Logging

Implementar:

- Serilog
- Application Insights

Registrar:

- Excepciones
- Advertencias
- Eventos de seguridad
- Intentos fallidos de autenticación

No registrar:

- Contraseñas
- Tokens
- Datos sensibles

---

# Auditoría

Todas las tablas deben incluir:

- CreatedBy
- CreatedDate
- UpdatedBy
- UpdatedDate
- IsActive

Implementar:

```csharp
AuditableEntity
```

como entidad base.

---

# Subida de Archivos

Validar:

- Extensión
- Tamaño
- Tipo MIME

Permitidos:

- pdf
- xlsx
- docx
- png
- jpg

Prohibidos:

- exe
- dll
- bat
- ps1

Tamaño máximo:

20 MB

---

# SignalR

Todo Hub debe requerir autenticación.

Validar permisos antes de:

- Conectarse
- Unirse a grupos
- Recibir eventos

Los hubs no deben contener lógica de negocio.

---

# Redis

Obligatorio:

- TLS habilitado
- Acceso privado

No exponer Redis a Internet.

---

# SQL Server

Utilizar:

- Azure SQL Database

Habilitar:

- TDE
- Auditoría
- Defender for SQL

Preferir:

- Private Endpoint

---

# Azure

Servicios mínimos de seguridad:

- Azure Key Vault
- Application Insights
- Microsoft Defender for Cloud

Recomendados:

- Azure WAF
- Front Door
- Private Endpoints

---

# Docker

Los contenedores deben:

- Ejecutarse como usuario no root
- Utilizar imágenes oficiales
- Exponer únicamente puertos necesarios

---

# CI/CD

Antes de desplegar:

- Ejecutar pruebas unitarias
- Ejecutar análisis de código
- Validar vulnerabilidades
- Validar exposición de secretos

Bloquear despliegues si existen vulnerabilidades críticas.

---

# Checklist de Seguridad

Todo proyecto generado debe incluir:

✅ JWT

✅ Refresh Tokens

✅ Roles

✅ FluentValidation

✅ HTTPS

✅ Key Vault

✅ Application Insights

✅ Serilog

✅ Auditoría

✅ CORS

✅ Rate Limiting

✅ Protección SQL Injection

✅ Protección XSS

✅ Health Checks

✅ Seguridad Docker

✅ Seguridad CI/CD
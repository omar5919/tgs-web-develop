# Estándares de Desarrollo

## Objetivo

Definir las convenciones de codificación obligatorias para todos los proyectos generados por este agente.

Estas reglas buscan:

- Consistencia
- Legibilidad
- Mantenibilidad
- Escalabilidad
- Facilidad de pruebas

---

# Idioma

## Documentación

Toda la documentación deberá generarse en español:

- README
- Diagramas
- Historias de usuario
- Casos de uso
- Comentarios funcionales

---

## Código

Todo el código deberá escribirse en inglés.

Ejemplos:

Correcto:

```csharp
CreateUserCommand
UserRepository
NotificationService
```

Incorrecto:

```csharp
CrearUsuarioComando
RepositorioUsuarios
ServicioNotificacion
```

---

# Principios Generales

Aplicar siempre:

- SOLID
- DRY
- KISS
- Clean Code
- Separation of Concerns

Evitar:

- Código duplicado
- Métodos gigantes
- Dependencias circulares
- Clases multipropósito

---

# Convenciones de Nombres

## Clases

Utilizar PascalCase.

Ejemplos:

```csharp
UserService
ProductRepository
InvoiceGenerator
```

---

## Métodos

Utilizar PascalCase.

Ejemplos:

```csharp
CreateUser()
GetById()
CalculateTotal()
```

---

## Variables

Utilizar camelCase.

Ejemplos:

```csharp
userName
totalAmount
createdDate
```

---

## Constantes

Utilizar PascalCase.

Ejemplo:

```csharp
public const int MaxFileSize = 20;
```

---

## Interfaces

Prefijo I.

Ejemplos:

```csharp
IUserService
IRepository
ICacheService
```

---

# Organización de Archivos

Mantener un archivo por clase.

Correcto:

```text
CreateUserCommand.cs
CreateUserHandler.cs
UserDto.cs
```

Incorrecto:

```text
UserClasses.cs
Utilities.cs
Helper.cs
```

---

# Métodos

## Tamaño

Preferentemente:

- Menos de 30 líneas

Máximo recomendado:

- 50 líneas

Los métodos extensos deben dividirse.

---

## Responsabilidad

Cada método debe tener una única responsabilidad.

Correcto:

```csharp
CreateUser()
```

Incorrecto:

```csharp
CreateUserAndSendEmailAndGenerateAuditAndUpdateCache()
```

---

# ASP.NET Core

## Controllers

Los Controllers deben ser delgados.

Solo deben:

- Recibir solicitudes
- Invocar MediatR
- Retornar respuestas

Ejemplo:

```csharp
[HttpPost]
public async Task<IActionResult> Create(
    CreateUserCommand command)
{
    var result = await _mediator.Send(command);

    return Ok(result);
}
```

No colocar lógica de negocio.

---

# CQRS

Todo caso de uso debe implementarse mediante:

- Command
- Query
- Handler

Ejemplo:

```text
CreateUserCommand
CreateUserHandler

GetUsersQuery
GetUsersHandler
```

---

# Validaciones

Utilizar FluentValidation.

Correcto:

```text
CreateUserCommandValidator
```

Incorrecto:

```csharp
if(string.IsNullOrEmpty(request.Name))
{
}
```

dentro del Handler.

---

# Async / Await

Obligatorio utilizar programación asíncrona.

Correcto:

```csharp
await repository.GetByIdAsync(id);
```

Incorrecto:

```csharp
repository.GetById(id);
```

cuando existe versión async.

---

# Nullability

Habilitar Nullable Reference Types.

Obligatorio:

```xml
<Nullable>enable</Nullable>
```

Ejemplo:

```csharp
string? phoneNumber;
```

---

# DTOs

No exponer entidades directamente.

Correcto:

```text
UserDto
ProductDto
OrderDto
```

Incorrecto:

```csharp
return User;
```

desde la entidad de dominio.

---

# Manejo de Errores

No capturar excepciones innecesariamente.

Incorrecto:

```csharp
try
{
}
catch(Exception ex)
{
    throw;
}
```

Utilizar middleware global.

Ejemplo:

```text
ExceptionMiddleware
```

---

# Logging

Utilizar:

- ILogger
- Serilog

Registrar:

- Información operativa
- Advertencias
- Errores

No registrar:

- Passwords
- Tokens
- Datos sensibles

---

# Dapper

Toda consulta debe ser parametrizada.

Correcto:

```csharp
var user = await connection.QueryFirstOrDefaultAsync<User>(
    sql,
    new { Id = id });
```

Incorrecto:

```csharp
var sql = $"SELECT * FROM Users WHERE Id={id}";
```

---

# SQL

## Convenciones

Tablas:

```sql
Users
Products
Orders
```

Columnas:

```sql
UserId
FirstName
CreatedDate
```

Procedimientos:

```sql
usp_User_Create
usp_User_Update
usp_User_Delete
```

---

# Entidades

Todas las entidades deben heredar de:

```csharp
AuditableEntity
```

Campos mínimos:

```csharp
CreatedBy
CreatedDate
UpdatedBy
UpdatedDate
IsActive
```

---

# Frontend Nuxt

## TypeScript

Obligatorio.

No utilizar:

```javascript
any
```

salvo justificación documentada.

---

# Componentes

Separar responsabilidades.

Correcto:

```text
components/users

UserCard.vue
UserList.vue
UserForm.vue
```

---

# Estado Global

Utilizar únicamente:

```text
Pinia
```

Prohibido:

```text
Vuex
```

---

# Consumo de APIs

Toda llamada HTTP debe estar en:

```text
/services
```

Correcto:

```text
UserService.ts
ProductService.ts
```

Incorrecto:

Realizar llamadas HTTP directamente desde componentes.

---

# Variables de Entorno

Nunca hardcodear valores.

Utilizar:

```env
API_URL=
SIGNALR_URL=
APP_VERSION=
```

---

# Comentarios

Comentar únicamente cuando aporte valor.

Correcto:

```csharp
// Se recalcula el stock debido a movimientos pendientes.
```

Incorrecto:

```csharp
// Asignar valor
name = request.Name;
```

---

# Pruebas Unitarias

Todo módulo debe permitir pruebas unitarias.

Cobertura mínima objetivo:

```text
80%
```

Casos obligatorios:

- Commands
- Queries
- Validators
- Services

---

# SonarQube

El código generado debe cumplir:

- Code Smells = 0 críticos
- Vulnerabilidades = 0 críticas
- Bugs = 0 críticos
- Duplicación < 3%

---

# Checklist de Calidad

Toda solución generada debe cumplir:

✅ Clean Architecture

✅ SOLID

✅ CQRS

✅ MediatR

✅ FluentValidation

✅ Nullable Enabled

✅ Async/Await

✅ DTOs

✅ Logging

✅ Middleware Global de Errores

✅ Dapper Parametrizado

✅ TypeScript Strict

✅ Pinia

✅ Variables de Entorno

✅ Pruebas Unitarias

✅ Código documentado

✅ SonarQube Ready
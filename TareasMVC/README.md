# TareasMVC – Aplicación de gestión de tareas

Aplicación web desarrollada con **ASP.NET Core MVC y C#** que permite a los usuarios organizar sus actividades mediante tareas, pasos y archivos adjuntos. Implementa autenticación de usuarios, persistencia de datos con SQL Server y operaciones CRUD mediante controladores y endpoints HTTP.

El proyecto está enfocado en la gestión organizada de actividades, con una interfaz dinámica que permite actualizar y ordenar la información sin recargar constantemente la página.

## Características principales

- **Gestión de tareas:** crear, consultar, editar y eliminar tareas.
- **Gestión de pasos:** agregar subtareas, editar descripciones, marcar actividades como completadas y eliminarlas.
- **Seguimiento del progreso:** visualizar la cantidad de pasos realizados y el porcentaje de avance de cada tarea.
- **Archivos adjuntos:** cargar, descargar, renombrar y eliminar archivos asociados a cada tarea.
- **Ordenamiento dinámico:** reorganizar tareas, pasos y archivos mediante arrastrar y soltar.
- **Autenticación de usuarios:** registro, inicio y cierre de sesión mediante ASP.NET Core Identity.
- **Administración de usuarios:** consultar usuarios y gestionar el rol de administrador.
- **Control de acceso:** cada usuario administra sus propias tareas y sus elementos relacionados.
- **Internacionalización:** soporte de interfaz en español e inglés.
- **Almacenamiento de archivos:** implementación de almacenamiento local y una alternativa basada en Azure Blob Storage.

## Tecnologías utilizadas

### Backend
- C#
- ASP.NET Core MVC (.NET 9)
- Entity Framework Core 9
- ASP.NET Core Identity
- SQL Server
- AutoMapper
- REST API

### Frontend
- HTML5
- CSS3
- JavaScript
- Bootstrap
- jQuery
- jQuery UI
- Knockout.js
- SweetAlert2

### Almacenamiento
- Sistema de archivos local
- Azure Blob Storage

## Arquitectura y estructura del proyecto

El proyecto utiliza una estructura basada en el patrón MVC, separando responsabilidades entre controladores, entidades, modelos, vistas y servicios.

```text
TareasMVC/
│
├── Controllers/
│   ├── HomeController.cs
│   ├── UsuariosController.cs
│   ├── TareasController.cs
│   ├── PasosController.cs
│   └── ArchivosController.cs
│
├── Entidades/
│   ├── Tarea.cs
│   ├── Paso.cs
│   └── ArchivoAdjunto.cs
│
├── Models/
│   ├── ViewModels
│   ├── DTOs
│   └── Modelos de apoyo
│
├── Servicios/
│   ├── ServicioUsuarios.cs
│   ├── IAlmacenadorArchivos.cs
│   ├── AlmacenadorArchivosLocal.cs
│   ├── AlmacenadorArchivosAzure.cs
│   ├── AutoMapperProfiles.cs
│   └── Constantes.cs
│
├── Views/
│   ├── Home/
│   ├── Usuarios/
│   └── Shared/
│
├── wwwroot/
│   ├── css/
│   ├── js/
│   └── archivosadjuntos/
│
├── Recursos/
│
├── appsettings.json
├── Program.cs
└── TareasMVC.csproj
```

## Modelo de datos

La aplicación utiliza tres entidades principales:

| Entidad | Descripción |
|---|---|
| Tarea | Almacena el título, descripción, fecha de creación y usuario propietario. |
| Paso | Representa las actividades individuales asociadas a una tarea. |
| ArchivoAdjunto | Almacena la información y ubicación de los archivos relacionados con una tarea. |

Las relaciones permiten mantener organizadas las actividades y sus recursos asociados.

## API y operaciones HTTP

El proyecto implementa endpoints para administrar la información mediante solicitudes HTTP.

| Controlador | Ruta base | Operaciones |
|---|---|---|
| TareasController | `/api/tareas` | GET, POST, PUT, DELETE y ordenamiento |
| PasosController | `/api/pasos` | POST, PUT, DELETE y ordenamiento |
| ArchivosController | `/api/archivos` | POST, PUT, DELETE y ordenamiento |

Las operaciones están vinculadas al usuario autenticado para controlar el acceso a sus propios recursos.

## Instalación y ejecución

### Requisitos previos

- Visual Studio 2022 o superior.
- .NET 9 SDK.
- SQL Server.
- SQL Server Management Studio (SSMS).
- Git.

### 1. Clonar el repositorio

```bash
git clone https://github.com/DeiCortez23/TareasMVC.git
```

### 2. Abrir el proyecto

Abre el archivo `TareasMVC.csproj` desde Visual Studio o accede a la carpeta del proyecto desde una terminal.

### 3. Configurar la conexión a SQL Server

La aplicación utiliza una cadena de conexión llamada `DefaultConnection`.

Configúrala mediante User Secrets para evitar publicar credenciales:

```bash
dotnet user-secrets set "ConnectionStrings:DefaultConnection" "Server=TU_SERVIDOR;Database=TareasMVC;Trusted_Connection=True;TrustServerCertificate=True"
```

Sustituye `TU_SERVIDOR` por el nombre de tu instancia de SQL Server.

### 4. Crear o actualizar la base de datos

Si el repositorio incluye las migraciones de Entity Framework Core, ejecuta:

```bash
dotnet ef database update
```

También puedes utilizar el Administrador de paquetes de NuGet en Visual Studio:

```powershell
Update-Database
```

### 5. Ejecutar la aplicación

Desde la terminal:

```bash
dotnet restore
dotnet run
```

O ejecuta el proyecto directamente desde Visual Studio utilizando IIS Express o el perfil de ejecución configurado.

## Configuración de almacenamiento

Por defecto, la aplicación utiliza `AlmacenadorArchivosLocal` para guardar los archivos adjuntos dentro de `wwwroot`.

También incluye una implementación alternativa con Azure Blob Storage (`AlmacenadorArchivosAzure`), que requiere configurar la cadena de conexión `AzureStorage` y seleccionar ese servicio en la configuración de dependencias de `Program.cs`.

## Aprendizajes y conceptos aplicados

Durante el desarrollo de este proyecto se trabajó con:

- Desarrollo de aplicaciones web utilizando ASP.NET Core MVC.
- Operaciones CRUD con Entity Framework Core.
- Diseño de entidades y relaciones en SQL Server.
- Implementación de autenticación y autorización con ASP.NET Core Identity.
- Desarrollo de endpoints para operaciones HTTP.
- Uso de DTOs y AutoMapper.
- Inyección de dependencias y separación de responsabilidades.
- Programación asíncrona con `async` y `await`.
- Manipulación dinámica de interfaces mediante JavaScript y Knockout.js.
- Gestión de archivos y servicios de almacenamiento.
- Organización y persistencia de información por usuario.

## Autor

**David Sánchez Cortez**

Ingeniero en Tecnologías de la Información y Comunicaciones | Desarrollador .NET Junior.

- GitHub: [DeiCortez23](https://github.com/DeiCortez23)
- LinkedIn: [David Cortez](https://www.linkedin.com/in/david-cortez-2650b63aa/)

---

Proyecto desarrollado con fines de aprendizaje y práctica de tecnologías .NET.
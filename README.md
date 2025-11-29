# Aplicación de gestión de usuarios y roles (Node.js + PostgreSQL)

Esta es una aplicación backend construida con **Node.js**, **Express** y **PostgreSQL**, enfocada en la administración de usuarios y roles. El proyecto implementa un modelo de datos estructurado con **Sequelize (ORM)**, permitiendo operaciones CRUD completas y aplicando buenas prácticas de conexión, modularización y validación.

El objetivo principal fue consolidar habilidades en **Express**, **Sequelize**, **PostgreSQL**, manejo de rutas REST, control de errores y estructura MVC simplificada.

## Características principales

- Conexión a PostgreSQL utilizando buenas prácticas.
- Modelos de datos para **Usuarios** y **Roles** mediante Sequelize.
- Operaciones CRUD completas:
  - Crear, listar, obtener por ID, actualizar y eliminar.
- Asociaciones **uno a muchos** entre Roles y Usuarios.
- Validaciones básicas y manejo de errores en rutas.
- Estructura de proyecto organizada por responsabilidad (`models/`, `controllers/`, `config/`).
- Variables de entorno para credenciales en `.env.demo`.

## Tecnologías utilizadas

- **Node.js**
- **Express**
- **PostgreSQL**
- **Sequelize**
- **Postman** (para pruebas)

## Estructura del proyecto

```
App de gestión de usuarios y roles
┣ 📂config
┃ ┗ 📜db.js
┣ 📂controllers
┃ ┗ 📜operaciones-CRUD.js
┣ 📂models
┃ ┣ 📜index.js
┃ ┣ 📜rol.js
┃ ┗ 📜usuario.js
┣ 📜.env.demo
┣ 📜app.js
┣ 📜package.json
┗ 📜README.md
```

## Configuración y ejecución

### 1️. Clonar el repositorio

```
git clone <url-del-repo>
cd <nombre-del-proyecto>
```

### 2. Instalar dependencias

`npm install`

### 3. Configurar variables de entorno

Renombra .env.demo → .env y completa:

```
DB_HOST=localhost
DB_USER=postgres
DB_PASSWORD=\*\*\*\*
DB_NAME=usuarios_roles
DB_PORT=5432
PORT=4020
```

### 4️. Ejecutar servidor

`npm run start`

Servidor por defecto: http://localhost:4020

## Pruebas con Postman

**A. Crear rol**

POST http://localhost:4020/roles

Body (JSON):

```json
{
  "nombre": "Administrador"
}
```

**B. Crear usuario**

POST http://localhost:4020/usuarios

Body (JSON):

```json
{
  "nombre": "Juan Pérez",
  "correo": "juan@example.com",
  "contrasena": "1234",
  "id_rol": 1
}
```

**C. Obtener datos**

- GET /usuarios → Listar usuarios
- GET /usuarios/:id → Obtener usuario por ID
- GET /roles → Listar roles
- GET /roles/:id → Obtener rol por ID

Ejemplo:

GET http://localhost:4020/usuarios/1

**D. Actualizar usuario**

PATCH http://localhost:4020/usuarios/1

Body (JSON):

```json
{
  "nuevoNombre": "Pedro",
  "nuevoCorreo": "pedro@example.com",
  "nuevaContrasena": "abcd123"
}
```

**E. Actualizar rol**

PATCH http://localhost:4020/roles/1

Body (JSON):

```json
{
  "nuevoNombre": "Editor"
}
```

**F. Eliminar registros**

- DELETE /usuarios/:id
- DELETE /roles/:id

Ejemplo:

DELETE http://localhost:4020/usuarios/1

**Notas:**

Las rutas incluyen validaciones básicas, puedes probar errores enviando datos incompletos o tipos incorrectos.

La base de datos debe existir antes de ejecutar el servidor.

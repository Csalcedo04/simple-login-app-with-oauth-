# Proyecto de Autenticación con Express, Passport y PostgreSQL

Este proyecto es una aplicación web que permite a los usuarios registrarse, iniciar sesión y enviar datos protegidos utilizando Express.js, Passport.js y una base de datos PostgreSQL. Los usuarios pueden autenticarse usando credenciales locales o a través de Google OAuth2.

## Características

- Registro de usuarios con hash de contraseñas utilizando bcrypt.
- Inicio de sesión local.
- Autenticación con Google OAuth2.
- Gestión de sesiones con `express-session`.
- Almacenamiento de datos de usuarios en PostgreSQL.
- Envío y visualización de "secretos" protegidos.

## Tecnologías Utilizadas

- Node.js
- Express.js
- Passport.js (Local y Google OAuth2)
- PostgreSQL
- bcrypt
- dotenv

## Configuración

### Requisitos Previos

- Node.js y npm instalados.
- PostgreSQL instalado y configurado.

### Instalación

1. Clona el repositorio:
    ```bash
    git clone https://github.com/tu-usuario/nombre-del-repositorio.git
    cd nombre-del-repositorio
    ```

2. Instala las dependencias:
    ```bash
    npm install
    ```

3. Crea un archivo `.env` en la raíz del proyecto con las siguientes variables de entorno:
    ```env
    SESSION_SECRET=tu_secreto_de_sesion
    PG_USER=tu_usuario_de_postgres
    PG_HOST=localhost
    PG_DATABASE=tu_base_de_datos
    PG_PASSWORD=tu_contraseña_de_postgres
    PG_PORT=5432
    GOOGLE_CLIENT_ID=tu_google_client_id
    GOOGLE_CLIENT_SECRET=tu_google_client_secret
    ```

4. Configura la base de datos PostgreSQL y crea la tabla de usuarios:
    ```sql
    CREATE TABLE users (
      id SERIAL PRIMARY KEY,
      email VARCHAR(255) UNIQUE NOT NULL,
      password VARCHAR(255) NOT NULL,
      secrets TEXT
    );
    ```

### Uso

1. Inicia el servidor:
    ```bash
    npm start
    ```

2. Abre tu navegador y visita `http://localhost:3000`.

### Rutas

- `/` - Página principal.
- `/login` - Página de inicio de sesión.
- `/register` - Página de registro.
- `/logout` - Cerrar sesión.
- `/secrets` - Página de secretos (requiere autenticación).
- `/submit` - Página para enviar secretos (requiere autenticación).
- `/auth/google` - Autenticación con Google.
- `/auth/google/secrets` - Redirección de Google OAuth2.

### Archivos
- `index.js` - Archivo principal del servidor.
- `public/` - Directorio para archivos estáticos.
- `views/` - Directorio para plantillas EJS.

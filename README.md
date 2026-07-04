# Colegio San Marcos API
Este proyecto es una API REST construida con Node.js y Express para la gestión del Colegio San Marcos. Utiliza Prisma ORM para interactuar de forma segura y eficiente con una base de datos PostgreSQL.

## Requisitos Previos
Antes de comenzar, asegúrate de tener instalado lo siguiente en tu equipo:

Node.js (Versión 20.x, 22.x o superior recomendada)

PostgreSQL (Instalado localmente o una instancia en la nube)

Un gestor de paquetes como npm (incluido con Node.js)

## Instalación y Configuración
Sigue estos pasos para levantar el entorno de desarrollo local:

### 1. Clonar el proyecto e instalar dependencias
Entra al directorio de tu proyecto y ejecuta el siguiente comando para descargar los módulos necesarios:

Bash
npm install
### 2. Configurar las Variables de Entorno
El proyecto requiere de ciertas variables para conectar con la base de datos y gestionar la seguridad.

Duplica el archivo .env.example y renombralo a .env.

Llena las variables con tus credenciales. Debería verse de la siguiente forma:

Fragmento de código
PORT=3000
API_KEY=tu_api_key_aqui
DATABASE_URL="postgresql://usuario:contraseña@localhost:5432/colegio_san_marcos?schema=public"
JWT_SECRET=tu_clave_secreta_para_tokens
### 3. Configurar la Base de Datos con Prisma
Una vez configurado el DATABASE_URL en tu .env, ejecuta las migraciones de Prisma para mapear y crear las tablas en tu base de datos:

Bash
npx prisma migrate dev
Nota: Esto también generará automáticamente el cliente de Prisma (@prisma/client) para que pueda ser utilizado por el código.

## Scripts Disponibles
En el archivo package.json se encuentran definidos los comandos necesarios para el ciclo de vida del proyecto:

npm run dev: Inicia el servidor de desarrollo utilizando la herramienta nativa --watch de Node.js. El servidor se reiniciará automáticamente cada vez que guardes un cambio en el código.

npx prisma studio: (Opcional) Abre una interfaz gráfica en tu navegador (http://localhost:5555) para explorar y editar los datos de tu base de datos de manera visual.

## Estructura de Endpoints Principales
El servidor expone sus rutas bajo el prefijo /api en el puerto configurado (por defecto http://localhost:3000). Las secciones principales mapeadas son:

Autenticación: http://localhost:3000/api/auth — Manejo de sesiones, login y registro respaldado por tokens JWT y encriptación bcryptjs.

Alumnos: http://localhost:3000/api/alumnos — Endpoints para la gestión y control escolar de los alumnos.

## Tecnologías Utilizadas
Backend: Node.js (Módulos ESM / type: "module") & Express 5

Base de Datos y ORM: PostgreSQL & Prisma ORM

Seguridad: JSON Web Tokens (jsonwebtoken) & bcryptjs

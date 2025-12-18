# Assessment - Sistema CRUD de Gestión de Clientes, Facturas y Transacciones

Sistema completo de gestión que permite administrar clientes, facturas, transacciones y generar reportes. Construido con una arquitectura cliente-servidor moderna usando Node.js, Express, PostgreSQL y Vanilla JavaScript.

## 📋 Descripción

Este proyecto es una aplicación web full-stack que proporciona un sistema CRUD (Crear, Leer, Actualizar, Eliminar) para gestionar:
- **Clientes**: Información de contacto y datos personales
- **Facturas**: Registro de facturas con montos facturados y pagados
- **Transacciones**: Seguimiento de pagos por plataforma
- **Reportes**: Análisis de datos financieros y estadísticas

## ✨ Características

- ✅ CRUD completo para clientes, facturas y transacciones
- ✅ Validación de datos en frontend y backend
- ✅ Interfaz de usuario responsive con pestañas
- ✅ API RESTful documentada con Postman
- ✅ Base de datos PostgreSQL con relaciones
- ✅ Reportes avanzados:
  - Total pagado por cliente
  - Facturas con saldo pendiente
  - Transacciones filtradas por plataforma
- ✅ Exportación de datos a CSV
- ✅ Mensajes de confirmación con SweetAlert2
- ✅ Hot reload en desarrollo (nodemon + Vite)

## 🛠️ Tecnologías

### Backend
- **Node.js** v18+ - Entorno de ejecución
- **Express** v5.1.0 - Framework web
- **PostgreSQL** - Base de datos relacional
- **pg** - Cliente PostgreSQL para Node.js
- **dotenv** - Gestión de variables de entorno
- **cors** - Manejo de CORS
- **bcryptjs** - Hash de contraseñas
- **multer** - Manejo de archivos
- **csv-parser** - Procesamiento de archivos CSV

### Frontend
- **Vite** v7.1.2 - Bundler y servidor de desarrollo
- **Vanilla JavaScript** - Sin frameworks
- **Axios** v1.11.0 - Cliente HTTP
- **SweetAlert2** v11.22.3 - Alertas y modales

### Base de Datos
- **PostgreSQL** - Sistema de gestión de base de datos
- **Supabase** - Hosting de PostgreSQL (opcional)

## 📦 Prerequisitos

Antes de comenzar, asegúrate de tener instalado:

- [Node.js](https://nodejs.org/) v18 o superior
- [npm](https://www.npmjs.com/) v9 o superior
- [PostgreSQL](https://www.postgresql.org/) v12 o superior
- Un cliente PostgreSQL (pgAdmin, DBeaver, etc.) o cuenta en [Supabase](https://supabase.com/)

## 🚀 Instalación

### 1. Clonar el repositorio

```bash
git clone https://github.com/Carturo8/Assessment.git
cd Assessment
```

### 2. Configurar el Backend

```bash
cd backend
npm install
```

### 3. Configurar el Frontend

```bash
cd ../frontend
npm install
```

### 4. Configurar la Base de Datos

#### Opción A: PostgreSQL Local

1. Conectarse a PostgreSQL y crear la base de datos ejecutando el script de schema desde el directorio raíz del proyecto:
```bash
cd /ruta/a/Assessment
psql -U postgres -f backend/database/schema/schema_data.sql
```

2. (Opcional) Cargar datos de prueba:
```bash
psql -U postgres -d pd_carlos_rojas_gosling -f backend/database/seeds/seed_data.sql
```

#### Opción B: Supabase

1. Crear un proyecto en [Supabase](https://supabase.com/)
2. Ir a SQL Editor y ejecutar el contenido de `backend/database/schema/schema_data.sql`
3. Obtener las credenciales de conexión

### 5. Configurar Variables de Entorno

Copiar el archivo de ejemplo y configurar las variables:

```bash
cd backend
cp .env.example .env
```

Editar el archivo `.env` con tus credenciales:

```env
# PostgreSQL Configuration
DB_HOST=tu-host.supabase.co
DB_USER=tu_usuario
DB_PASSWORD=tu_contraseña
DB_NAME=postgres
DB_PORT=6543

# Server Configuration
PORT=3000
```

## 🎯 Uso

### Iniciar el Backend

```bash
cd backend
npm run dev
```

El servidor estará disponible en `http://localhost:3000`

### Iniciar el Frontend

En otra terminal:

```bash
cd frontend
npm run dev
```

La aplicación estará disponible en `http://localhost:5173`

### Acceder a la Aplicación

1. Abrir el navegador en `http://localhost:5173`
2. Usar las pestañas para navegar entre Clientes, Facturas y Transacciones
3. Realizar operaciones CRUD en cada sección

## 📡 API Endpoints

### Clientes

| Método | Endpoint | Descripción |
|--------|----------|-------------|
| GET | `/api/clients` | Obtener todos los clientes |
| GET | `/api/clients/:id` | Obtener un cliente por ID |
| POST | `/api/clients` | Crear un nuevo cliente |
| PUT | `/api/clients/:id` | Actualizar un cliente |
| DELETE | `/api/clients/:id` | Eliminar un cliente |

### Facturas

| Método | Endpoint | Descripción |
|--------|----------|-------------|
| GET | `/api/invoices` | Obtener todas las facturas |
| GET | `/api/invoices/:id` | Obtener una factura por ID |
| POST | `/api/invoices` | Crear una nueva factura |
| PUT | `/api/invoices/:id` | Actualizar una factura |
| DELETE | `/api/invoices/:id` | Eliminar una factura |

### Transacciones

| Método | Endpoint | Descripción |
|--------|----------|-------------|
| GET | `/api/transactions` | Obtener todas las transacciones |
| GET | `/api/transactions/:id` | Obtener una transacción por ID |
| POST | `/api/transactions` | Crear una nueva transacción |
| PUT | `/api/transactions/:id` | Actualizar una transacción |
| DELETE | `/api/transactions/:id` | Eliminar una transacción |

### Plataformas

| Método | Endpoint | Descripción |
|--------|----------|-------------|
| GET | `/api/platforms` | Obtener todas las plataformas |
| POST | `/api/platforms` | Crear una nueva plataforma |

### Reportes

| Método | Endpoint | Descripción |
|--------|----------|-------------|
| GET | `/api/reports/clients-total-paid` | Total pagado por cada cliente |
| GET | `/api/reports/invoices-pending-balance` | Facturas con saldo pendiente |
| GET | `/api/reports/transactions-by-platform?platform=nombre` | Transacciones por plataforma |

## 📁 Estructura del Proyecto

```
Assessment/
├── backend/
│   ├── config/
│   │   └── db.js                 # Configuración de PostgreSQL
│   ├── controllers/
│   │   ├── clientsController.js  # Lógica de negocio de clientes
│   │   ├── invoicesController.js # Lógica de negocio de facturas
│   │   ├── transactionsController.js
│   │   ├── platformsController.js
│   │   └── reportsController.js  # Generación de reportes
│   ├── database/
│   │   ├── schema/
│   │   │   └── schema_data.sql   # Esquema de la base de datos
│   │   └── seeds/
│   │       └── seed_data.sql     # Datos de prueba
│   ├── data_exports/             # Exportaciones CSV
│   ├── routes/
│   │   ├── clientsRoutes.js      # Rutas de clientes
│   │   ├── invoicesRoutes.js     # Rutas de facturas
│   │   ├── transactionsRoutes.js
│   │   ├── platformsRoutes.js
│   │   └── reportsRoutes.js
│   ├── .env.example              # Plantilla de variables de entorno
│   ├── api-crud-reports.postman_collection.json
│   ├── package.json
│   └── server.js                 # Punto de entrada del servidor
├── frontend/
│   ├── src/
│   │   ├── api.js                # Cliente HTTP (Axios)
│   │   ├── main.js               # Lógica principal del frontend
│   │   └── style.css             # Estilos de la aplicación
│   ├── index.html                # Página principal
│   └── package.json
├── docs/
│   └── Assessment_ERM.png        # Diagrama Entidad-Relación
├── .gitignore
├── LICENSE                       # Licencia MIT
└── README.md                     # Este archivo
```

## 🗄️ Modelo de Base de Datos

El sistema utiliza 4 tablas principales:

### Clients
```sql
- client_id (SERIAL PRIMARY KEY)
- client_name (VARCHAR)
- client_address (VARCHAR)
- client_phone (VARCHAR)
- client_email (VARCHAR UNIQUE)
```

### Platforms
```sql
- platform_id (SERIAL PRIMARY KEY)
- platform_name (VARCHAR)
```

### Invoices
```sql
- invoice_id (VARCHAR PRIMARY KEY)
- invoice_date (TEXT)
- invoiced_amount (NUMERIC)
- amount_paid (NUMERIC)
- client_id (FK -> clients)
```

### Transactions
```sql
- transaction_id (VARCHAR PRIMARY KEY)
- transaction_date (TIMESTAMP)
- transaction_amount (NUMERIC)
- transaction_status (VARCHAR)
- transaction_type (VARCHAR)
- client_id (FK -> clients)
- platform_id (FK -> platforms)
- invoice_id (FK -> invoices)
```

Ver el diagrama completo en `docs/Assessment_ERM.png`

## 🔧 Scripts Disponibles

### Backend

```bash
npm run dev    # Iniciar servidor en modo desarrollo (con nodemon)
npm start      # Iniciar servidor en modo producción
```

### Frontend

```bash
npm run dev     # Iniciar servidor de desarrollo con Vite
npm run build   # Construir para producción
npm run preview # Vista previa de la build de producción
```

## 🧪 Pruebas con Postman

El proyecto incluye una colección de Postman en:
```
backend/api-crud-reports.postman_collection.json
```

Para usar la colección:

1. Importar el archivo en Postman
2. Configurar la variable de entorno `baseUrl` (ejemplo: `http://localhost:3000`)
3. Ejecutar las peticiones de prueba

## 🔒 Seguridad

- Las credenciales se gestionan mediante variables de entorno
- Conexión SSL a PostgreSQL habilitada
- CORS configurado para desarrollo
- ⚠️ **Nota**: Antes de desplegar en producción, asegúrate de:
  - Configurar todas las variables de entorno en el archivo `.env`
  - Configurar CORS para dominios específicos
  - Implementar autenticación y autorización
  - Usar HTTPS

## 📝 Variables de Entorno

| Variable | Descripción | Ejemplo |
|----------|-------------|---------|
| `DB_HOST` | Host de PostgreSQL | `localhost` o `tu-proyecto.supabase.co` |
| `DB_USER` | Usuario de la base de datos | `postgres` |
| `DB_PASSWORD` | Contraseña de la base de datos | `tu_contraseña` |
| `DB_NAME` | Nombre de la base de datos | `postgres` |
| `DB_PORT` | Puerto de PostgreSQL | `5432` o `6543` (Supabase) |
| `PORT` | Puerto del servidor Express | `3000` |

## 🤝 Contribuir

Las contribuciones son bienvenidas. Por favor:

1. Fork el proyecto
2. Crea una rama para tu feature (`git checkout -b feature/AmazingFeature`)
3. Commit tus cambios (`git commit -m 'Add some AmazingFeature'`)
4. Push a la rama (`git push origin feature/AmazingFeature`)
5. Abre un Pull Request

## 📄 Licencia

Este proyecto está bajo la Licencia MIT - ver el archivo [LICENSE](LICENSE) para más detalles.

## 👤 Autor

**Carlos Rojas**

- GitHub: [@Carturo8](https://github.com/Carturo8)

## 🙏 Agradecimientos

- Express.js por el excelente framework web
- Vite por la herramienta de desarrollo ultrarrápida
- Supabase por el hosting de PostgreSQL
- Comunidad de Node.js y JavaScript

---

⭐️ Si este proyecto te fue útil, considera darle una estrella en GitHub

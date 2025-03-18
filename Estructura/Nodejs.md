Estructura de carpetas organizada y escalable para un proyecto **backend** con **Node.js** y **Express**:

```
📦 mi-proyecto-backend
├── 📂 node_modules/         --> Dependencias instaladas con npm
├── 📂 src/                  --> Código fuente principal
│    ├── 📂 config/          --> Configuración (base de datos, variables de entorno, etc.)
│    │     └── db.js        --> Conexión a la base de datos
│    │     └── env.js       --> Variables de entorno
│    │
│    ├── 📂 controllers/     --> Lógica de negocio (controladores)
│    │     └── user.controller.js
│    │     └── auth.controller.js
│    │
│    ├── 📂 models/          --> Modelos (Esquemas de la base de datos)
│    │     └── user.model.js
│    │
│    ├── 📂 routes/          --> Definición de las rutas (endpoints)
│    │     └── user.routes.js
│    │     └── auth.routes.js
│    │     └── index.js     --> Enrutador principal
│    │
│    ├── 📂 middlewares/     --> Middlewares (autenticación, validaciones, etc.)
│    │     └── auth.middleware.js
│    │     └── error.middleware.js
│    │
│    ├── 📂 services/        --> Servicios (lógica independiente, como envío de correos, etc.)
│    │     └── email.service.js
│    │     └── auth.service.js
│    │
│    ├── 📂 utils/           --> Utilidades y funciones de ayuda
│    │     └── logger.js    --> Registro de logs
│    │     └── response.js  --> Respuestas personalizadas
│    │
│    └── app.js             --> Configuración de Express
│
├── 📂 tests/                --> Pruebas (unitarias e integración)
│    └── user.test.js
│
├── .env                    --> Variables de entorno
├── .gitignore              --> Archivos a excluir de Git
├── package.json            --> Información del proyecto y dependencias
├── package-lock.json       --> Bloqueo de versiones
└── README.md               --> Documentación del proyecto
```

### ✅ **Explicación de las carpetas principales**:

- **`src/`**: Código fuente del proyecto.
  - **`config/`**: Configuraciones globales (base de datos, variables de entorno).
  - **`controllers/`**: Gestiona la lógica de negocio, recibe peticiones y da respuestas.
  - **`models/`**: Define los modelos y esquemas de la base de datos (MongoDB, MySQL, etc.).
  - **`routes/`**: Define las rutas del API (RESTful).
  - **`middlewares/`**: Funciones intermedias como validación de JWT, manejo de errores, etc.
  - **`services/`**: Lógica reusable como enviar correos, cifrado de contraseñas, etc.
  - **`utils/`**: Funciones de utilidad (logs, respuestas estándar, etc.).
  - **`app.js`**: Configuración de Express (middlewares, rutas, etc.).

### 📌 **Comandos útiles**:

1. **Instalar dependencias básicas**:

   ```bash
   npm init -y
   npm install express dotenv mongoose cors
   npm install nodemon --save-dev
   ```

2. **Script para ejecutar el servidor con `nodemon`** (en `package.json`):
   ```json
   "scripts": {
     "dev": "nodemon src/app.js"
   }
   ```

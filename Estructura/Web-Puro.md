**Estructura organizada y escalable** para un proyecto web puro con **HTML, CSS y JavaScript**. Es ideal para sitios estáticos o dinámicos sin necesidad de frameworks o librerías adicionales.

```
📦 mi-proyecto-web
├── 📂 assets/              --> Archivos estáticos (imágenes, íconos, fuentes, etc.)
│    ├── 📂 css/           --> Archivos de estilos
│    │    ├── main.css    --> Estilos principales
│    │    └── reset.css   --> Normalización de estilos (opcional)
│    │
│    ├── 📂 js/            --> Archivos JavaScript
│    │    ├── main.js     --> Lógica principal
│    │    ├── utils.js    --> Funciones auxiliares
│    │    └── dom.js      --> Manipulación del DOM
│    │
│    ├── 📂 img/          --> Imágenes del proyecto
│    │    ├── logo.png
│    │    └── banner.jpg
│    │
│    └── 📂 fonts/        --> Fuentes personalizadas (si las usas)
│         └── Roboto.woff2
│
├── 📂 pages/              --> Páginas adicionales (si el sitio tiene más de una)
│    ├── about.html      --> Página "Acerca de"
│    ├── contact.html    --> Página de contacto
│    └── services.html   --> Página de servicios
│
├── 📂 components/         --> Componentes HTML reutilizables (cabecera, pie de página, etc.)
│    ├── header.html     --> Encabezado
│    ├── footer.html     --> Pie de página
│    └── navbar.html     --> Barra de navegación
│
├── index.html            --> Página principal (home)
├── .gitignore            --> Archivos a ignorar en Git
└── README.md             --> Documentación del proyecto
```

---

### ✅ **Explicación de las carpetas principales:**

- **`assets/`**: Contiene los recursos estáticos del proyecto:
  - **`css/`**: Archivos de estilos (CSS puro o preprocesador como SASS).
  - **`js/`**: Scripts de JavaScript para agregar interactividad.
  - **`img/`**: Imágenes (logos, banners, etc.).
  - **`fonts/`**: Fuentes personalizadas (si las necesitas).
- **`pages/`**: Páginas adicionales del sitio web (para mantener limpio el `index.html`).

- **`components/`**: Fragmentos HTML reutilizables (como un **header** o **footer**), que puedes **incluir** manualmente o mediante **JavaScript**.

---

### 📌 **Estructura de ejemplo para el `index.html`:**

```html
<!DOCTYPE html>
<html lang="es">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Mi Proyecto Web</title>
    <link rel="stylesheet" href="assets/css/reset.css" />
    <link rel="stylesheet" href="assets/css/main.css" />
  </head>

  <body>
    <!-- Encabezado -->
    <header id="header"></header>

    <main>
      <h1>Bienvenido a Mi Proyecto Web</h1>
      <p>Este es un proyecto con HTML, CSS y JavaScript puro.</p>
    </main>

    <!-- Pie de página -->
    <footer id="footer"></footer>

    <script src="assets/js/dom.js"></script>
    <script src="assets/js/main.js"></script>
  </body>
</html>
```

---

### 📘 **Ejemplo de carga de un componente con JavaScript (`dom.js`):**

```js
// Cargar el header y footer dinámicamente
document.addEventListener('DOMContentLoaded', () => {
  loadComponent('#header', 'components/header.html');
  loadComponent('#footer', 'components/footer.html');
});

function loadComponent(selector, url) {
  fetch(url)
    .then((res) => res.text())
    .then((html) => {
      document.querySelector(selector).innerHTML = html;
    })
    .catch((err) => console.error(`Error al cargar ${url}`, err));
}
```

---

### 🚀 **Cómo iniciar el proyecto localmente:**

Si quieres visualizar tu proyecto con un servidor local (recomendado para probar **fetch** y rutas relativas):

1. Si tienes **Python** instalado:

   ```bash
   python -m http.server 8000
   ```

   (Luego visita: http://localhost:8000)

2. Si tienes **Node.js** instalado:
   ```bash
   npx serve
   ```

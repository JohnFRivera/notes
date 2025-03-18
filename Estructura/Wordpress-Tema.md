# Estructuras para carpetas de temas personalizados de Wordpress

## ¿Qué es?

En **WordPress**, un tema es un conjunto de archivos que define el diseño y la funcionalidad visual de un sitio web. Los temas controlan cómo se muestran los elementos en la pantalla, desde la disposición de los menús y los colores hasta la tipografía y la estructura general de las páginas.

## Características principales de los temas:

1. **Diseño visual:** Los temas establecen la apariencia del sitio, permitiendo personalizar colores, fuentes y estilos sin modificar el contenido.

2. **Plantillas de página:** Muchos temas incluyen plantillas prediseñadas para páginas específicas, como la página de inicio, sobre nosotros o contacto.

3. **Widgets y áreas personalizables:** Los temas pueden tener áreas configurables, como barras laterales, pies de página y encabezados.

4. **Compatibilidad con plugins:** Los temas están diseñados para integrarse con plugins y extender la funcionalidad del sitio.

5. **Responsividad:** La mayoría de los temas modernos son responsive, es decir, adaptan su diseño a dispositivos móviles y tabletas.

## Estructura de sus carpetas:

```bash
/mi-tema
│
├── assets/              # Recursos estáticos como CSS, JS, imágenes, fuentes, etc.
│   ├── css/             # Archivos CSS
│   ├── js/              # Archivos JavaScript
│   ├── images/          # Imágenes
│   ├── fonts/           # Fuentes personalizadas
│   └── vendor/          # Librerías externas (como Bootstrap o Swiper)
│
├── templates/           # Plantillas reutilizables
│   ├── parts/           # Partes comunes como encabezado, pie de página, barra lateral
│   ├── components/      # Componentes específicos como tarjetas, sliders, etc.
│   └── layouts/         # Diseños generales como página completa, blog, etc.
│
├── inc/                 # Archivos de funciones PHP
│   ├── setup.php        # Configuración básica del tema (soporte para menús, widgets, etc.)
│   ├── enqueues.php     # Registro y carga de estilos y scripts
│   ├── customizer.php   # Configuración del personalizador de WordPress
│   ├── shortcodes.php   # Definición de shortcodes
│   └── helpers.php      # Funciones utilitarias
│
├── languages/           # Archivos de traducción (.mo, .po)
│
├── woocommerce/         # Personalizaciones de WooCommerce (si aplica)
│
├── style.css            # Archivo de cabecera del tema
├── functions.php        # Punto de entrada principal para funciones del tema
├── index.php            # Plantilla principal de WordPress
├── header.php           # Encabezado global
├── footer.php           # Pie de página global
├── sidebar.php          # Barra lateral global
├── page.php             # Plantilla base para páginas
├── single.php           # Plantilla base para entradas individuales
├── archive.php          # Plantilla base para archivos (categorías, etiquetas)
├── 404.php              # Plantilla para la página de error 404
├── search.php           # Plantilla para resultados de búsqueda
└── screenshot.png       # Imagen de vista previa del tema en el administrador de WordPress
```

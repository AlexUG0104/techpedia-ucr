## Techpedia UCR 📚

Una enciclopedia temática interactiva sobre tecnologías esenciales para estudiantes de Informática.

Este proyecto se desarrolló para el curso IF7102 - Multimedios de la Universidad de Costa Rica.

## Tecnologías

- Vue 3 (Composition API / `<script setup>`)
- Vite
- HTML5, JavaScript
- CSS (archivos modulares en `src/css/` y `src/style.css`)
- JSON para los datos (en `public/data/technologies.json`)

## Funcionalidades principales

- Buscador en tiempo real
- Filtro por categoría
- Modo oscuro/claro
- Reproducción de audios descriptivos
- Diseño responsivo
- Tarjetas dinámicas con detalles en modal

## Estructura del proyecto

```text
.
├── index.html
├── package.json
├── README.md
├── REFERENCIAS.md
├── vite.config.js
├── public/
│   ├── audio/                 # archivos de audio (.mp3)
│   └── data/
│       └── technologies.json  # datos de las tecnologías
└── src/
    ├── App.vue
    ├── main.js
    ├── style.css
    ├── assets/                # imágenes y recursos estáticos
    ├── components/
    │   ├── AudioButton.vue
    │   ├── Footer.vue
    │   ├── Header.vue
    │   ├── HeroPanel.vue
    │   ├── SearchFilter.vue
    │   ├── TechCard.vue
    │   ├── TechModal.vue
    │   └── ThemeToggle.vue
    └── css/
        ├── audio-button.css
        ├── base.css
        ├── footer.css
        ├── header.css
        ├── hero-panel.css
        ├── index.css
        ├── layout.css
        ├── search-filter.css
        ├── tech-card.css
        ├── tech-modal.css
        └── theme-toggle.css
```

## Ejecutar localmente

1. Instalar dependencias:

```bash
npm install
```

2. Levantar servidor de desarrollo:

```bash
npm run dev
```

Abre el navegador en la URL que muestre la consola (por ejemplo `http://localhost:5173`).

## Despliegue (GitHub Pages)

Si utilizas GitHub Pages para alojar el proyecto mediante Vite, asegúrate de que `vite.config.js` tenga definida la opción `base` correspondiente al nombre de tu repositorio (`base: '/techpedia-ucr/'`).

Comandos para compilar y desplegar:

```bash
# Compilar el proyecto para producción
npm run build

# Desplegar la carpeta dist a la rama gh-pages
npx gh-pages -d dist
```

## Capturas de pantalla

A continuación se muestran capturas representativas de la interfaz de la enciclopedia:

### 1. Vista Principal (Header con Logo UCR y Modo Claro)
![Vista Principal en Escritorio](./public/img/Cap/Principal.png)

### 2. Detalle de Tecnología en Modal (Soporte de Tema Oscuro)
![Modal de Detalles](./public/img/Cap/Modal.png)


## Notas del Proyecto

- Los datos de las tecnologías están estructurados en `public/data/technologies.json`.
- Los audios descriptivos en formato MP3 están alojados localmente en `public/audio/`.
- Las imágenes vectoriales (SVG) de los logotipos de tecnologías se alojan localmente en `public/img/tech/`.
- El logotipo oficial de la cabecera y el favicon se sirven desde `public/img/logoArriba.png`.
- La modularización de estilos CSS se ubica en `src/css/` y es enlazada a través de `src/style.css`.


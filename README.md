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

Si usas GitHub Pages con Vite, asegúrate de que `vite.config.js` tenga la opción `base` correcta. Comandos comunes:

```bash
npm run build
npx gh-pages -d dist
```

## Notas

- Los datos de las tecnologías están en `public/data/technologies.json`.
- Los audios descriptivos se guardan en `public/audio/`.
- Los estilos están organizados en `src/css/` y `src/style.css`.

Si quieres, ajusto el README para agregar capturas o instrucciones de despliegue más detalladas.


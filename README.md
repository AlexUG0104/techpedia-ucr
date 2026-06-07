# Techpedia UCR 📚

Una **Enciclopedia Temática Interactiva** sobre tecnologías esenciales para estudiantes de Informática. 

Este proyecto fue desarrollado para el curso **IF7102 - Multimedios** de la Universidad de Costa Rica, cumpliendo con los requerimientos de la **Opción 4: Enciclopedia Temática Interactiva**.

## 🚀 Tecnologías y Framework Utilizado

El proyecto está construido utilizando herramientas modernas de desarrollo web:
- **Vue 3** (Composition API con `<script setup>`)
- **Vite** (como herramienta de compilación ultrarrápida)
- **Vanilla CSS** (con variables para modo oscuro/claro y diseño responsive)
- **HTML5 & JavaScript**
- **JSON** para la carga dinámica de datos (mediante la API `fetch()`)

## ✨ Funcionalidades

- ✅ **Buscador en tiempo real:** Filtra tecnologías mientras escribes.
- ✅ **Filtro por categoría:** Permite visualizar por Frontend, Backend, Herramientas, etc.
- ✅ **Modo Oscuro/Claro:** Interfaz amigable para la vista en diferentes entornos.
- ✅ **Soporte Multimedia:** Integración de audios descriptivos y uso de iconos externos para representar tecnologías.
- ✅ **Diseño Responsivo:** Adaptable a dispositivos móviles, tablets y pantallas de escritorio.
- ✅ **Tarjetas Dinámicas:** Tarjetas interactivas con *badges* de dificultad y enlaces a la documentación oficial.

## 📂 Estructura del Proyecto

```text
src/
├── components/
│   ├── Header.vue         # Cabecera con título y botón de tema
│   ├── SearchFilter.vue   # Componente de búsqueda y filtro
│   ├── TechCard.vue       # Tarjeta individual por tecnología
│   ├── AudioButton.vue    # Botón reproductor de audio descriptivo
│   ├── ThemeToggle.vue    # Interruptor de modo oscuro/claro
│   └── Footer.vue         # Pie de página
├── App.vue                # Componente raíz que maneja el estado y fetch
├── main.js                # Punto de entrada de Vue
└── style.css              # Estilos globales y paleta de la UCR

public/
├── data/
│   └── technologies.json  # Base de datos en JSON con mínimo 10 entradas
├── audio/                 # Archivos de audio descriptivo (.mp3)
├── favicon.svg           # Ícono del sitio
└── icons.svg             # SVG de iconos adicionales
```

## 📦 Instrucciones de Instalación y Uso

Si clonas este repositorio, sigue estos pasos para ejecutar la aplicación localmente:

1. **Instalar dependencias**:
   ```bash
   npm install
   ```

2. **Ejecutar el servidor de desarrollo**:
   ```bash
   npm run dev
   ```

3. Abre tu navegador en la URL que indique la consola (usualmente `http://localhost:5173`).

## 🖼️ Capturas de Pantalla

*(Nota: Agrega aquí las capturas de pantalla de la aplicación terminada)*

## 🔗 Enlaces

- **Repositorio en GitHub**: https://github.com/AlexUG0104/techpedia-ucr.git
- **Sitio en vivo (GitHub Pages)**: https://alexug0104.github.io/techpedia-ucr/

## 🌐 Despliegue en GitHub Pages

El proyecto ya está preparado para GitHub Pages con `vite.config.js` configurado en:

```js
base: '/techpedia-ucr/'
```

Pasos básicos para actualizar el sitio:
1. Ejecuta `npm run build`.
2. Publica la carpeta `dist` en GitHub Pages, por ejemplo con `npx gh-pages -d dist`.
3. Verifica el sitio en: https://alexug0104.github.io/techpedia-ucr/


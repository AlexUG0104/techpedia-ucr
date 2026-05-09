# Techpedia UCR 📚

Una **Enciclopedia Temática Interactiva** sobre tecnologías esenciales para estudiantes de Informática. 

Este proyecto fue desarrollado para el curso **IF7102 - Multimedios** de la Universidad de Costa Rica.

## 🚀 Tecnologías y Framework Utilizado

El proyecto está construido utilizando herramientas modernas de desarrollo web:
- **Vue 3** (Composition API con `<script setup>`)
- **Vite** (como herramienta de compilación ultrarrápida)
- **Vanilla CSS** (con variables para modo oscuro/claro y diseño responsive)
- **HTML5 & JavaScript**

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

- **Repositorio en GitHub**: [https://github.com/TU-USUARIO/techpedia-ucr](https://github.com/TU-USUARIO/techpedia-ucr)
- **Sitio en vivo (GitHub Pages)**: [https://TU-USUARIO.github.io/techpedia-ucr/](https://TU-USUARIO.github.io/techpedia-ucr/) *(Se agregará una vez desplegado)*

## 🌐 Cómo publicar en GitHub Pages

Al final del proyecto, para publicar en GitHub Pages:
1. En `vite.config.js`, agrega: `base: '/techpedia-ucr/'`.
2. Sube tus cambios a GitHub.
3. Configura GitHub Actions para construir el proyecto o sube la carpeta `dist` manualmente a la rama `gh-pages`.

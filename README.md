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
- ✅ **Soporte Multimedia:** Integración de imágenes representativas y audios descriptivos para al menos 3 entradas.
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
└── images/                # Recursos gráficos e íconos locales
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

- **Repositorio en GitHub**: [https://github.com/TU-USUARIO/techpedia-ucr](https://github.com/TU-USUARIO/techpedia-ucr)
- **Sitio en vivo (GitHub Pages)**: [https://TU-USUARIO.github.io/techpedia-ucr/](https://TU-USUARIO.github.io/techpedia-ucr/) *(Se agregará una vez desplegado)*

## 🌐 Cómo publicar en GitHub Pages

Al final del proyecto, para publicar en GitHub Pages se configurará lo siguiente:
1. En `vite.config.js`, agregar: `base: '/techpedia-ucr/'`.
2. Subir los cambios a GitHub.
3. Configurar GitHub Actions para construir el proyecto o subir la carpeta `dist` manualmente a la rama `gh-pages`.

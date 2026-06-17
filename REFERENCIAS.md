# Referencias y Justificación del Proyecto

Este documento detalla la justificación del diseño, la elección de las tecnologías del proyecto y las referencias bibliográficas utilizadas durante el desarrollo.

---

## 1. Justificación de la Opción Seleccionada (Enciclopedia Temática Interactiva)

Se seleccionó la **Opción 4: Enciclopedia Temática Interactiva** debido a su alto valor pedagógico y técnico en el marco del desarrollo web actual:
* **Enfoque Educativo**: Permite sintetizar y estructurar conceptos tecnológicos clave para estudiantes de la carrera de Informática, actuando como un portal de consulta rápida de libre acceso.
* **Teoría del Aprendizaje Multimedia**: Siguiendo los principios de Richard Mayer sobre el aprendizaje multimedia, la enciclopedia integra múltiples canales de entrada sensorial (canal visual mediante textos descriptivos y logotipos; canal auditivo mediante narraciones grabadas en formato MP3; y canal audiovisual mediante videos de apoyo de YouTube), facilitando una asimilación más profunda de los conceptos expuestos.
* **Navegación Intuitiva**: El diseño fomenta la interactividad mediante filtrados dinámicos por categoría y un buscador en tiempo real, mejorando la usabilidad y la experiencia de usuario general.

---

## 2. Justificación Técnica de la Arquitectura Seleccionada

* **Vue 3 (Composition API & `<script setup>`)**:
  - Se eligió Vue 3 por su excelente sistema de reactividad basado en proxies. Permite realizar búsquedas y filtrados de manera instantánea, sin recargar la página y consumiendo muy pocos recursos en el cliente.
  - La arquitectura basada en componentes reutilizables (`TechCard`, `TechModal`, `AudioButton`, etc.) facilita el aislamiento de responsabilidades, facilitando las pruebas individuales y la mantenibilidad del código.
* **Separación de Datos (JSON Cargado Dinámicamente)**:
  - En lugar de codificar la información de las tecnologías en los componentes (hardcoding), los datos se alojan en un archivo `technologies.json` de manera independiente.
  - Esto simula el consumo de un servicio web (API REST) y permite escalar la enciclopedia en el futuro añadiendo nuevas tecnologías en el JSON sin necesidad de modificar o recompilar el código fuente de Vue.
* **CSS Puro (Vanilla CSS Modulado)**:
  - Se evitó el uso de frameworks pesados (como Bootstrap o Tailwind) con el objetivo de demostrar un dominio completo de las técnicas modernas de maquetación en CSS (como CSS Grid y Flexbox) y mantener el bundle final sumamente ligero.
  - Cada componente posee su archivo de estilo modularizado dentro de `src/css/`, permitiendo modificaciones independientes del estilo visual.
* **Persistencia del Estado y Accesibilidad**:
  - Se implementó `localStorage` para guardar el estado del tema oscuro, lo que garantiza que la preferencia visual del usuario persista entre recargas.
  - Se incluyeron mejoras de accesibilidad como el cierre del modal detallado mediante la tecla `Escape` y el bloqueo del scroll de fondo, asegurando el cumplimiento de prácticas web recomendadas.

---

## 3. Referencias Bibliográficas y Recursos Utilizados

1. **Documentación Oficial de Vue.js 3**  
   - Base conceptual para el ciclo de vida de componentes (`onMounted`, `onUnmounted`), reactividad (`ref`, `computed`) y paso de parámetros (`props`, `emits`).  
   - [https://vuejs.org/guide/introduction.html](https://vuejs.org/guide/introduction.html)

2. **Documentación Oficial de Vite**  
   - Referencia para la configuración de rutas base (`base` path) para la correcta compilación y enrutamiento en servidores de producción y GitHub Pages.  
   - [https://vitejs.dev/guide/](https://vitejs.dev/guide/)

3. **MDN Web Docs (Mozilla Developer Network)**  
   - Manuales técnicos utilizados para la API Fetch (carga del archivo JSON de datos), la API de Audio de HTML5 (control de reproducción de sonido offline) y guías avanzadas de diseño CSS (CSS Variables, Flexbox, y CSS Grid responsivo).  
   - [https://developer.mozilla.org/es/](https://developer.mozilla.org/es/)

4. **Fuentes de Recursos Gráficos (Logotipos de Tecnologías)**  
   - Los logotipos vectoriales de las tecnologías se obtuvieron y descargaron localmente del repositorio de **Devicon**, un proyecto open-source de íconos técnicos libres de derechos de autor.  
   - [https://devicon.dev/](https://devicon.dev/)
   - El logotipo y favicon oficiales del proyecto provienen de los recursos institucionales de la **Universidad de Costa Rica (UCR)**.

5. **Fuentes de Audio**  
   - Los audios descriptivos adjuntos a las tecnologías se generaron de forma digital e independiente a través del conversor de voz a texto inteligente de Google Cloud (Text-to-Speech API).

6. **Uso de IA de Apoyo**  
   - Se utilizaron asistentes de inteligencia artificial (Gemini/ChatGPT) únicamente como apoyo para la estructuración metodológica del proyecto, el planteamiento CSS inicial de transiciones en modales y la optimización de contraste en modo oscuro. El código lógico del proyecto fue desarrollado y acoplado de forma individual para satisfacer los objetivos prácticos del curso IF7102.

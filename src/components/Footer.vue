<template>
  <footer class="app-footer">
    <div class="footer-content">
      <p>&copy; {{ new Date().getFullYear() }} Techpedia UCR - Curso IF7102 Multimedios</p>
      <p class="credits">Desarrollado para la Universidad de Costa Rica</p>
    </div>
  </footer>
</template>

<style scoped>
.app-footer {
  background-color: var(--primary-color);
  color: white;
  text-align: center;
  padding: 2rem 0;
  margin-top: 4rem;
}

.footer-content {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}

.footer-content p {
  margin: 0.5rem 0;
}

.credits {
  font-size: 0.9rem;
  opacity: 0.8;
}
</style>

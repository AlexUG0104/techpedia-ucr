<template>
  <header class="app-header">
    <div class="header-container">
      <div class="logo-area">
        <h1>Techpedia <span>UCR</span></h1>
        <p class="subtitle">Enciclopedia Temática Interactiva</p>
      </div>
      <ThemeToggle :isDark="isDark" @toggleTheme="$emit('toggleTheme')" />
    </div>
  </header>
</template>

<script setup>
import ThemeToggle from './ThemeToggle.vue';

defineProps({
  isDark: {
    type: Boolean,
    required: true
  }
});

defineEmits(['toggleTheme']);
</script>

<style scoped>
.app-header {
  background-color: var(--primary-color);
  color: white;
  padding: 1.5rem 0;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.header-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.logo-area h1 {
  margin: 0;
  font-size: 2rem;
  font-weight: 800;
  letter-spacing: -0.5px;
}

.logo-area h1 span {
  color: var(--accent-color);
}

.subtitle {
  margin: 5px 0 0;
  font-size: 1rem;
  opacity: 0.9;
}

@media (max-width: 600px) {
  .header-container {
    flex-direction: column;
    text-align: center;
    gap: 1rem;
  }
}
</style>

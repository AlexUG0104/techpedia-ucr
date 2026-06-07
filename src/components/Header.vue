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

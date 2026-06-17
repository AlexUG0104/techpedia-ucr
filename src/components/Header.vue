<template>
  <header class="app-header">
    <div class="header-container">
      <div class="logo-area">
        <img :src="`${baseUrl}img/logoArriba.png`" alt="Logo UCR" class="header-logo" />
        <div class="logo-text">
          <h1>Techpedia <span>UCR</span></h1>
          <p class="subtitle">Enciclopedia Temática Interactiva</p>
        </div>
      </div>
      <ThemeToggle :isDark="isDark" @toggleTheme="$emit('toggleTheme')" />
    </div>
  </header>
</template>

<script setup>
import ThemeToggle from './ThemeToggle.vue';

const baseUrl = import.meta.env.BASE_URL;

defineProps({
  isDark: {
    type: Boolean,
    required: true
  }
});

defineEmits(['toggleTheme']);
</script>

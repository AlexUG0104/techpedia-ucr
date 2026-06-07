<template>
  <button class="theme-toggle" @click="emit('toggleTheme')" :aria-label="isDark ? 'Cambiar a modo claro' : 'Cambiar a modo oscuro'">
    <span v-if="isDark" class="icon">☀️</span>
    <span v-else class="icon">🌙</span>
  </button>
</template>

<script setup>
defineProps({
  isDark: {
    type: Boolean,
    required: true
  }
});

const emit = defineEmits(['toggleTheme']);
</script>

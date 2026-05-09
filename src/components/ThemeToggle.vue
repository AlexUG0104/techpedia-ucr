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

<style scoped>
.theme-toggle {
  background: transparent;
  border: 2px solid var(--text-color);
  color: var(--text-color);
  border-radius: 50%;
  width: 40px;
  height: 40px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: all 0.3s ease;
  font-size: 1.2rem;
}

.theme-toggle:hover {
  background: var(--text-color);
  color: var(--bg-color);
  transform: scale(1.1);
}
</style>

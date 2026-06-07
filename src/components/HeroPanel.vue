<template>
  <section class="hero-panel">
    <div class="hero-copy">
      <p class="eyebrow">Explora y aprende</p>
      <h2>Techpedia UCR: enciclopedia temática interactiva</h2>
      <p class="hero-text">Descubre tecnologías clave para el desarrollo web y herramientas de programación con fichas rápidas, audios descriptivos y recursos didácticos. Filtra, busca y accede a información clara al instante.</p>
    </div>

    <div class="hero-stats">
      <div class="stat-card">
        <span class="stat-value">{{ total }}</span>
        <p class="stat-label">Tecnologías</p>
      </div>
      <div class="stat-card">
        <span class="stat-value">{{ categories }}</span>
        <p class="stat-label">Categorías</p>
      </div>
      <div class="stat-card">
        <span class="stat-value">{{ audioCount }}</span>
        <p class="stat-label">Audios disponibles</p>
      </div>
    </div>
  </section>
</template>

<script setup>
const props = defineProps({
  total: {
    type: Number,
    required: true
  },
  categories: {
    type: Number,
    required: true
  },
  audioCount: {
    type: Number,
    required: true
  }
});
</script>

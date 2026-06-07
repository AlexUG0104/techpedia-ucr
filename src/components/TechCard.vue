<template>
  <article class="tech-card">
    <div class="card-header">
      <img :src="tech.image" :alt="tech.name" class="tech-image" />
      <div class="tech-badges">
        <span class="badge category" :class="tech.category.toLowerCase().replace(' ', '-')">
          {{ tech.category }}
        </span>
        <span class="badge difficulty" :class="tech.difficulty.toLowerCase()">
          {{ tech.difficulty }}
        </span>
      </div>
    </div>
    
    <div class="card-body">
      <h3>{{ tech.name }}</h3>
      <p class="description">{{ tech.description }}</p>
    </div>
    
    <div class="card-footer">
      <AudioButton v-if="tech.audio" :audioSrc="tech.audio" />
      <div v-else class="spacer"></div>
      
      <button @click="$emit('open-modal', tech)" class="link-btn">
        Ver más 🔗
      </button>
    </div>
  </article>
</template>

<script setup>
import AudioButton from './AudioButton.vue';

defineProps({
  tech: {
    type: Object,
    required: true
  }
});

defineEmits(['open-modal']);
</script>

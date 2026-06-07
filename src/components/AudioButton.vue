<template>
  <button 
    class="audio-btn" 
    @click.stop="toggleAudio" 
    :class="{ 'playing': isPlaying }"
    :aria-label="isPlaying ? 'Pausar audio' : 'Reproducir audio'"
  >
    <span class="icon">{{ isPlaying ? '⏸️' : '▶️' }}</span>
    <span class="text">{{ isPlaying ? 'Pausar' : 'Escuchar' }}</span>
  </button>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

const props = defineProps({
  audioSrc: {
    type: String,
    required: true
  }
});

const isPlaying = ref(false);
let audio = null;

const toggleAudio = () => {
  if (!audio) return;
  
  if (isPlaying.value) {
    audio.pause();
  } else {
    audio.play();
  }
  isPlaying.value = !isPlaying.value;
};

onMounted(() => {
  if (props.audioSrc) {
    audio = new Audio(`${import.meta.env.BASE_URL}audio/${props.audioSrc}`);
    audio.addEventListener('ended', () => {
      isPlaying.value = false;
    });
  }
});

onUnmounted(() => {
  if (audio) {
    audio.pause();
    audio.removeEventListener('ended', () => {});
    audio = null;
  }
});
</script>

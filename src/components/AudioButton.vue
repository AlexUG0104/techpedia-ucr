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
    audio = new Audio(`/audio/${props.audioSrc}`);
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

<style scoped>
.audio-btn {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  background-color: var(--secondary-color);
  color: white;
  border: none;
  padding: 0.5rem 1rem;
  border-radius: 20px;
  cursor: pointer;
  font-weight: 600;
  transition: all 0.3s ease;
  font-size: 0.9rem;
}

.audio-btn:hover {
  background-color: var(--accent-color);
  transform: translateY(-2px);
}

.audio-btn.playing {
  background-color: var(--accent-color);
  animation: pulse 1.5s infinite;
}

@keyframes pulse {
  0% { box-shadow: 0 0 0 0 rgba(234, 179, 8, 0.7); }
  70% { box-shadow: 0 0 0 10px rgba(234, 179, 8, 0); }
  100% { box-shadow: 0 0 0 0 rgba(234, 179, 8, 0); }
}
</style>

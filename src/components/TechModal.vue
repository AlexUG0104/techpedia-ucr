<template>
  <div class="modal-overlay" @click.self="$emit('close')">
    <div class="modal-container">
      <button class="close-button" @click="$emit('close')">&times;</button>
      
      <div class="modal-content" v-if="tech">
        <!-- Header -->
        <div class="modal-header">
          <img :src="`${baseUrl}${tech.image}`" :alt="tech.name" class="modal-tech-image" />
          <div class="modal-title-group">
            <h2>{{ tech.name }}</h2>
            <div class="modal-badges">
              <span class="badge category" :class="tech.category.toLowerCase().replace(' ', '-')">{{ tech.category }}</span>
              <span class="badge difficulty" :class="tech.difficulty.toLowerCase()">{{ tech.difficulty }}</span>
            </div>
          </div>
        </div>

        <!-- Tabs -->
        <div class="modal-tabs">
          <button 
            :class="['tab-btn', { active: activeTab === 'info' }]" 
            @click="activeTab = 'info'">
            Información
          </button>
          <button 
            :class="['tab-btn', { active: activeTab === 'video' }]" 
            @click="activeTab = 'video'">
            Video
          </button>
          <button 
            :class="['tab-btn', { active: activeTab === 'resources' }]" 
            @click="activeTab = 'resources'">
            Recursos
          </button>
        </div>

        <!-- Tab Content: Info -->
        <div v-if="activeTab === 'info'" class="tab-content scrollable">
          <section class="info-section">
            <h3>¿Qué es {{ tech.name }}?</h3>
            <p>{{ tech.detailedDescription || tech.description }}</p>
          </section>

          <section class="info-section" v-if="tech.purpose">
            <h3>¿Para qué sirve?</h3>
            <p>{{ tech.purpose }}</p>
          </section>

          <div class="features-grid" v-if="tech.features || tech.advantages">
            <section class="info-card" v-if="tech.features">
              <h3>Características Principales</h3>
              <ul>
                <li v-for="(feature, idx) in tech.features" :key="idx">{{ feature }}</li>
              </ul>
            </section>
            
            <section class="info-card" v-if="tech.advantages">
              <h3>Ventajas</h3>
              <ul>
                <li v-for="(adv, idx) in tech.advantages" :key="idx">{{ adv }}</li>
              </ul>
            </section>
          </div>

          <section class="info-section code-section" v-if="tech.codeExample">
            <h3>Ejemplo de código</h3>
            <pre><code>{{ tech.codeExample }}</code></pre>
          </section>

          <section class="info-section curiosities" v-if="tech.curiosities">
            <h3>💡 ¿Sabías que...?</h3>
            <ul>
              <li v-for="(curiosity, idx) in tech.curiosities" :key="idx">{{ curiosity }}</li>
            </ul>
          </section>
        </div>

        <!-- Tab Content: Video -->
        <div v-if="activeTab === 'video'" class="tab-content video-container">
          <iframe 
            v-if="tech.youtubeId"
            :src="`https://www.youtube.com/embed/${tech.youtubeId}`" 
            title="YouTube video player" 
            frameborder="0" 
            allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
            allowfullscreen>
          </iframe>
          <div v-else class="no-data">
            <p>No hay video disponible para esta tecnología.</p>
          </div>
        </div>

        <!-- Tab Content: Resources -->
        <div v-if="activeTab === 'resources'" class="tab-content">
          <div class="resources-list">
            <a :href="tech.officialUrl" target="_blank" rel="noopener noreferrer" class="resource-card primary">
              <span class="icon">📄</span>
              <div class="resource-text">
                <h4>Documentación Oficial</h4>
                <p>Visita el sitio oficial de {{ tech.name }}</p>
              </div>
            </a>
            
            <template v-if="tech.resources">
              <a v-for="(res, idx) in tech.resources" :key="idx" :href="res.url" target="_blank" rel="noopener noreferrer" class="resource-card">
                <span class="icon">📚</span>
                <div class="resource-text">
                  <h4>{{ res.title }}</h4>
                  <p>{{ res.type }}</p>
                </div>
              </a>
            </template>
          </div>
        </div>

      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

const baseUrl = import.meta.env.BASE_URL;

const props = defineProps({
  tech: {
    type: Object,
    required: true
  }
});

const emit = defineEmits(['close']);

const activeTab = ref('info');

const handleKeyDown = (e) => {
  if (e.key === 'Escape') {
    emit('close');
  }
};

// Prevenir el scroll del body y escuchar la tecla Escape cuando el modal está abierto
onMounted(() => {
  document.body.style.overflow = 'hidden';
  window.addEventListener('keydown', handleKeyDown);
});

onUnmounted(() => {
  document.body.style.overflow = '';
  window.removeEventListener('keydown', handleKeyDown);
});
</script>

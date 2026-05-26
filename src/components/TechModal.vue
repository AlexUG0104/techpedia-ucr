<template>
  <div class="modal-overlay" @click.self="$emit('close')">
    <div class="modal-container">
      <button class="close-button" @click="$emit('close')">&times;</button>
      
      <div class="modal-content" v-if="tech">
        <!-- Header -->
        <div class="modal-header">
          <img :src="tech.image" :alt="tech.name" class="modal-tech-image" />
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

const props = defineProps({
  tech: {
    type: Object,
    required: true
  }
});

defineEmits(['close']);

const activeTab = ref('info');

// Prevenir el scroll del body cuando el modal está abierto
onMounted(() => {
  document.body.style.overflow = 'hidden';
});

onUnmounted(() => {
  document.body.style.overflow = '';
});
</script>

<style scoped>
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background: rgba(0, 0, 0, 0.5);
  backdrop-filter: blur(8px);
  -webkit-backdrop-filter: blur(8px);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
  padding: 20px;
  animation: fadeIn 0.3s ease;
}

.modal-container {
  background: var(--card-bg, #ffffff);
  width: 100%;
  max-width: 900px;
  max-height: 90vh;
  display: flex;
  flex-direction: column;
  position: relative;
  overflow: hidden;
  border-radius: 24px;
  box-shadow: 0 30px 60px -15px rgba(0, 0, 0, 0.4), 0 0 0 1px rgba(255, 255, 255, 0.05);
  animation: scaleUp 0.4s cubic-bezier(0.16, 1, 0.3, 1);
  border: 1px solid var(--border-color);
}

.modal-content {
  display: flex;
  flex-direction: column;
  flex: 1;
  overflow: hidden;
}

.close-button {
  position: absolute;
  top: 20px;
  right: 20px;
  background: rgba(0,0,0,0.05);
  border: none;
  font-size: 1.5rem;
  width: 40px;
  height: 40px;
  border-radius: 50%;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  color: var(--text-color);
  transition: all 0.2s;
  z-index: 10;
}

.close-button:hover {
  background: rgba(239, 68, 68, 0.1);
  color: #ef4444;
  transform: rotate(90deg);
}

.modal-header {
  display: flex;
  align-items: center;
  gap: 24px;
  padding: 30px 40px;
  background: var(--card-header-bg, #f8fafc);
  border-bottom: 1px solid var(--border-color);
  flex-shrink: 0;
}

.modal-tech-image {
  width: 80px;
  height: 80px;
  object-fit: contain;
  filter: drop-shadow(0 4px 8px rgba(0,0,0,0.1));
}

.modal-title-group h2 {
  margin: 0 0 10px 0;
  font-size: 2.2rem;
  color: var(--text-color);
}

.modal-badges {
  display: flex;
  gap: 10px;
}

.badge {
  font-size: 0.8rem;
  padding: 0.4rem 1rem;
  border-radius: 20px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

/* Category Colors - Copiados de TechCard */
.badge.category { background-color: var(--secondary-color); color: white; }
.badge.frontend { background-color: #3b82f6; }
.badge.backend { background-color: #10b981; }
.badge.herramientas { background-color: #8b5cf6; }
.badge.bases-de-datos { background-color: #f59e0b; }
.badge.seguridad { background-color: #ef4444; }

/* Difficulty Colors */
.badge.básico { background-color: #dcfce7; color: #166534; }
.badge.intermedio { background-color: #fef08a; color: #854d0e; }
.badge.avanzado { background-color: #fee2e2; color: #991b1b; }

:global(.dark-mode) .badge.básico { background-color: #14532d; color: #bbf7d0; }
:global(.dark-mode) .badge.intermedio { background-color: #713f12; color: #fef08a; }
:global(.dark-mode) .badge.avanzado { background-color: #000000; color: #ffffff; border: 1px solid #333; }

.modal-tabs {
  display: flex;
  padding: 0 40px;
  background: var(--card-header-bg, #f8fafc);
  border-bottom: 1px solid var(--border-color);
  flex-shrink: 0;
}

.tab-btn {
  background: transparent;
  border: none;
  padding: 15px 25px;
  font-size: 1rem;
  font-weight: 600;
  color: var(--text-muted);
  cursor: pointer;
  position: relative;
  transition: color 0.3s;
}

.tab-btn:hover {
  color: var(--text-color);
}

.tab-btn.active {
  color: var(--secondary-color);
}

.tab-btn.active::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 3px;
  background: var(--secondary-color);
  border-radius: 3px 3px 0 0;
}

.tab-content {
  flex: 1;
  padding: 40px;
  overflow-y: auto;
  color: var(--text-color);
  scroll-behavior: smooth;
}

.info-section {
  margin-bottom: 30px;
}

.info-section h3 {
  color: var(--secondary-color);
  margin-bottom: 15px;
  font-size: 1.4rem;
}

.info-section p {
  line-height: 1.7;
  font-size: 1.05rem;
}

.features-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 20px;
  margin-bottom: 30px;
}

@media (max-width: 768px) {
  .features-grid {
    grid-template-columns: 1fr;
  }
}

.info-card {
  background: rgba(128, 128, 128, 0.03);
  padding: 24px;
  border-radius: 16px;
  border: 1px solid var(--border-color);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.info-card:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.05);
}

.info-card h3 {
  color: var(--text-color);
  margin-bottom: 15px;
  font-size: 1.25rem;
}

.info-card ul, .curiosities ul {
  padding-left: 20px;
  line-height: 1.6;
}

.info-card li, .curiosities li {
  margin-bottom: 8px;
}

.code-section pre {
  background: #1e1e1e;
  color: #d4d4d4;
  padding: 20px;
  border-radius: 12px;
  overflow-x: auto;
  font-family: 'Fira Code', monospace;
  font-size: 0.95rem;
  line-height: 1.5;
}

.curiosities {
  background: rgba(245, 158, 11, 0.08);
  padding: 24px;
  border-radius: 16px;
  border-left: 4px solid #f59e0b;
  transition: transform 0.3s ease;
}

.curiosities:hover {
  transform: scale(1.01);
}

.curiosities h3 {
  color: #d97706;
}

:global(.dark-mode) .curiosities h3 {
  color: #fbbf24;
}

/* Video Tab */
.video-container {
  display: flex;
  flex-direction: column;
  height: 100%;
}

.video-container iframe {
  width: 100%;
  aspect-ratio: 16 / 9;
  border-radius: 12px;
  box-shadow: 0 10px 20px rgba(0,0,0,0.1);
}

.no-data {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 200px;
  color: var(--text-muted);
  font-size: 1.2rem;
  background: rgba(128, 128, 128, 0.05);
  border-radius: 12px;
}

/* Resources Tab */
.resources-list {
  display: flex;
  flex-direction: column;
  gap: 15px;
}

.resource-card {
  display: flex;
  align-items: center;
  gap: 20px;
  padding: 20px;
  background: rgba(128, 128, 128, 0.05);
  border: 1px solid var(--border-color);
  border-radius: 12px;
  text-decoration: none;
  color: var(--text-color);
  transition: all 0.3s;
}

.resource-card:hover {
  transform: translateY(-3px);
  box-shadow: 0 10px 20px rgba(0,0,0,0.05);
  border-color: var(--secondary-color);
}

.resource-card.primary {
  background: rgba(37, 99, 235, 0.05);
  border-color: var(--secondary-color);
}

.resource-card .icon {
  font-size: 2rem;
}

.resource-text h4 {
  margin: 0 0 5px 0;
  font-size: 1.2rem;
  color: var(--secondary-color);
}

.resource-text p {
  margin: 0;
  color: var(--text-muted);
}

/* Animaciones */
@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

@keyframes scaleUp {
  from { 
    opacity: 0; 
    transform: scale(0.95) translateY(20px); 
  }
  to { 
    opacity: 1; 
    transform: scale(1) translateY(0); 
  }
}

/* Scrollbar minimalista y moderno */
.scrollable::-webkit-scrollbar {
  width: 6px;
}

.scrollable::-webkit-scrollbar-track {
  background: rgba(0, 0, 0, 0.02);
  border-radius: 8px;
}

:global(.dark-mode) .scrollable::-webkit-scrollbar-track {
  background: rgba(255, 255, 255, 0.02);
}

.scrollable::-webkit-scrollbar-thumb {
  background: rgba(128, 128, 128, 0.3);
  border-radius: 8px;
}

.scrollable::-webkit-scrollbar-thumb:hover {
  background: rgba(128, 128, 128, 0.6);
}
</style>

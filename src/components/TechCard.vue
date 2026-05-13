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
      
      <a :href="tech.officialUrl" target="_blank" rel="noopener noreferrer" class="link-btn">
        Ver más 🔗
      </a>
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
</script>

<style scoped>
.tech-card {
  background: var(--card-bg);
  border-radius: 16px;
  overflow: hidden;
  box-shadow: 0 10px 20px var(--shadow-color);
  transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
  display: flex;
  flex-direction: column;
  height: 100%;
  border: 1px solid var(--border-color);
}

.tech-card:hover {
  transform: translateY(-10px);
  box-shadow: 0 15px 30px var(--shadow-color);
  border-color: var(--secondary-color);
}

.card-header {
  padding: 1.5rem;
  background: var(--card-header-bg);
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  border-bottom: 1px solid var(--border-color);
}

.tech-image {
  width: 60px;
  height: 60px;
  object-fit: contain;
  filter: drop-shadow(0 4px 6px rgba(0,0,0,0.1));
}

.tech-badges {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  align-items: flex-end;
}

.badge {
  font-size: 0.75rem;
  padding: 0.3rem 0.8rem;
  border-radius: 12px;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

/* Category Colors */
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

/* Ajuste oscuro para los badges de dificultad */
:global(.dark-mode) .badge.básico { background-color: #14532d; color: #bbf7d0; }
:global(.dark-mode) .badge.intermedio { background-color: #713f12; color: #fef08a; }
:global(.dark-mode) .badge.avanzado { background-color: #000000; color: #ffffff; border: 1px solid #333; }

.card-body {
  padding: 1.5rem;
  flex-grow: 1;
}

.card-body h3 {
  margin: 0 0 1rem 0;
  font-size: 1.5rem;
  color: var(--text-color);
}

.description {
  color: var(--text-muted);
  line-height: 1.6;
  font-size: 0.95rem;
  margin: 0;
}

.card-footer {
  padding: 1.2rem 1.5rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  border-top: 1px solid var(--border-color);
  background: var(--card-bg);
}

.link-btn {
  text-decoration: none;
  color: var(--secondary-color);
  font-weight: 600;
  font-size: 0.9rem;
  transition: all 0.3s;
  padding: 0.5rem 1rem;
  border-radius: 8px;
  background: rgba(37, 99, 235, 0.1);
}

.link-btn:hover {
  background: var(--secondary-color);
  color: white;
}

.spacer {
  flex: 1;
}
</style>

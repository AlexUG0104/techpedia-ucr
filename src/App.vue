<template>
  <div class="app-wrapper">
    <Header :isDark="darkMode" @toggleTheme="toggleTheme" />

    <main class="main-content">
      <HeroPanel
        :total="totalTechnologies"
        :categories="categoryCount"
        :audioCount="audioCount"
      />

      <SearchFilter 
        v-model:searchTerm="searchTerm"
        v-model:selectedCategory="selectedCategory"
        :categories="availableCategories"
      />

      <div v-if="loading" class="status-message">
        <div class="loader"></div>
        <p>Cargando tecnologías...</p>
      </div>
      
      <div v-else-if="error" class="status-message error">
        <p>Error al cargar los datos: {{ error }}</p>
      </div>

      <div v-else-if="filteredTechnologies.length === 0" class="status-message empty">
        <p>No se encontraron tecnologías que coincidan con la búsqueda.</p>
      </div>

      <div v-else class="cards-grid">
        <TechCard 
          v-for="tech in filteredTechnologies" 
          :key="tech.id" 
          :tech="tech" 
          @open-modal="openModal"
        />
      </div>
    </main>

    <Footer />

    <!-- Modal de Detalles -->
    <Teleport to="body">
      <TechModal 
        v-if="selectedTech" 
        :tech="selectedTech" 
        @close="closeModal" 
      />
    </Teleport>
  </div>
</template>

<script setup>
import { ref, computed, onMounted, watch } from 'vue';
import Header from './components/Header.vue';
import HeroPanel from './components/HeroPanel.vue';
import SearchFilter from './components/SearchFilter.vue';
import TechCard from './components/TechCard.vue';
import TechModal from './components/TechModal.vue';
import Footer from './components/Footer.vue';

// Variables reactivas
const technologies = ref([]);
const searchTerm = ref('');
const selectedCategory = ref('');
const darkMode = ref(false);
const loading = ref(true);
const error = ref(null);
const selectedTech = ref(null);

const openModal = (tech) => {
  selectedTech.value = tech;
};

const closeModal = () => {
  selectedTech.value = null;
};

// Alternar tema y aplicarlo al body
const toggleTheme = () => {
  darkMode.value = !darkMode.value;
  if (darkMode.value) {
    document.body.classList.add('dark-mode');
  } else {
    document.body.classList.remove('dark-mode');
  }
};

// Cargar datos al montar el componente
onMounted(async () => {
  try {
    const response = await fetch(`${import.meta.env.BASE_URL}data/technologies.json`);
    if (!response.ok) {
      throw new Error(`HTTP error! status: ${response.status}`);
    }
    const data = await response.json();
    technologies.value = data;
    loading.value = false;
  } catch (err) {
    console.error("Error fetching data:", err);
    error.value = err.message;
    loading.value = false;
  }
});

// Computed properties
const availableCategories = computed(() => {
  const categories = new Set(technologies.value.map(t => t.category));
  return Array.from(categories).sort();
});

const filteredTechnologies = computed(() => {
  return technologies.value.filter(tech => {
    const matchesSearch = tech.name.toLowerCase().includes(searchTerm.value.toLowerCase()) || 
                          tech.description.toLowerCase().includes(searchTerm.value.toLowerCase());
    const matchesCategory = selectedCategory.value === '' || tech.category === selectedCategory.value;
    return matchesSearch && matchesCategory;
  });
});

const totalTechnologies = computed(() => technologies.value.length);
const categoryCount = computed(() => availableCategories.value.length);
const audioCount = computed(() => technologies.value.filter(t => t.audio).length);
</script>

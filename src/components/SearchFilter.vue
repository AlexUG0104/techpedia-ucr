<template>
  <div class="search-filter-section">
    <div class="search-box">
      <input 
        type="text" 
        :value="searchTerm" 
        @input="$emit('update:searchTerm', $event.target.value)"
        placeholder="Buscar tecnología..." 
        class="search-input"
      />
    </div>
    
    <div class="filter-box">
      <select 
        :value="selectedCategory"
        @change="$emit('update:selectedCategory', $event.target.value)"
        class="category-select"
      >
        <option value="">Todas las categorías</option>
        <option v-for="category in categories" :key="category" :value="category">
          {{ category }}
        </option>
      </select>
    </div>
  </div>
</template>

<script setup>
defineProps({
  searchTerm: {
    type: String,
    required: true
  },
  selectedCategory: {
    type: String,
    required: true
  },
  categories: {
    type: Array,
    required: true
  }
});

defineEmits(['update:searchTerm', 'update:selectedCategory']);
</script>

<style scoped>
.search-filter-section {
  display: flex;
  gap: 1rem;
  margin: 2rem 0;
  background: var(--card-bg);
  padding: 1.5rem;
  border-radius: 12px;
  box-shadow: 0 4px 15px var(--shadow-color);
  transition: all 0.3s ease;
}

.search-box {
  flex: 2;
}

.filter-box {
  flex: 1;
}

.search-input, .category-select {
  width: 100%;
  padding: 0.8rem 1.2rem;
  font-size: 1rem;
  border: 2px solid var(--border-color);
  border-radius: 8px;
  background-color: var(--input-bg);
  color: var(--text-color);
  transition: all 0.3s ease;
  font-family: inherit;
}

.search-input:focus, .category-select:focus {
  outline: none;
  border-color: var(--secondary-color);
  box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.2);
}

@media (max-width: 768px) {
  .search-filter-section {
    flex-direction: column;
  }
}
</style>

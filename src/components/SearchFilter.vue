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

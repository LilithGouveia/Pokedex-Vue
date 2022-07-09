<script setup>
import { ref, onMounted, computed, watch } from 'vue';
import api from '../apis/api.vue';
const filterText = ref('');
const filteredPokemon = computed(() => {
  return api;
});
</script>

<template>
  <input
    v-model="filterText"
    type="input"
    placeholder="Search"
    name="search"
    id="search"
    required
  />
</template>

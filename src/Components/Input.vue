<script setup>
import { ref, onMounted, computed, watch } from 'vue';
// Tratamento de erro caso o input esteja vazio.
const handleInput = e => {
  if (!e.target.value) {
    searchResults.value = [];
  }
}

</script>

<template>
  <section @submit.prevent="searchPokemon" class="input">
    <input placeholder="Search" v-model="query" @input="handleInput"/>
  </section>
</template>

<style>
/* #app {

} */
</style>

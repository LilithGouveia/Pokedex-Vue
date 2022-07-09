<script setup>
import { ref, onMounted, computed, watch } from 'vue';
import api from '../apis/api.vue'
const filterText = ref("");
const filteredPokemon = computed(() => {
  return api
})
</script>

<template>
  <div class="form__group field">
    <input type="input" class="form__field" placeholder="Name" name="name" id='name' required />
    <label for="name" class="form__label">Name</label>
  </div>
</template>

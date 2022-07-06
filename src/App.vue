<script setup>
import { ref, onMounted, computed, watch } from 'vue';
import Input from './Components/Input.vue';

const query = ref('');
const pokemonsList = ref([]);
const searchResults = ref([]);
const pokeID = 1;
// organização da lista
const pokemonsResult = computed(() => {
  return pokemonsList.value.sort((a, b) => {
    a.title.localecompare(b.title);
  });
});
// requisição da api
const pokedexApi = () => {
  const url = `https://pokeapi.co/api/v2/pokemon/${pokeID}`;
  fetch(url)
    .then((res) => res.json())
    .then((res) => {
      searchResults.value = res.results;
    });
};
// Tratamento de erro caso o input esteja vazio.
const handleInput = (e) => {
  if (!e.target.value) {
    searchResults.value = [];
  }
};
//  adicionando pokemons a tela
const addPokemon = (pokemon) => {
  searchResults.value = [];
  query.value = '';
  pokemonsList.push({
    name: pokemon.name,
    image: pokemon.sprites.front_default,
    id: pokemon.id,
  });
};

localStorage.setItem('pokedex', JSON.stringify(pokemonsList.value));

onMounted(() => {
  pokemonsList.value = JSON.parse(localStorage.getItem('pokedex')) || [];
});
</script>

<template>
  <main class="app">
    <header @submit.prevent="searchResults" class="input">
      <input placeholder="Search" v-model="query" @input="handleInput" />
    </header>
    
    <p>Desenvolvido pela mestre pokémon: Lili Gouveia</p>
  </main>
</template>

<style></style>

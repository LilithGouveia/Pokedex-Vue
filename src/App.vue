<script>
  import GetPokemon from '../src/apis/api.vue';
  import Card from '../src/Components/Card.vue';
  export default {
    name: 'app',
    components: {
    GetPokemon,
    Card
},
  };
</script>

<template>
  <main class="app">
    <header @submit.prevent="searchResults" class="input">
      <input placeholder="Search" />
    </header>
    <GetPokemon />
    <p>Desenvolvido pela mestre pokémon: Lili Gouveia</p>
  </main>
</template>

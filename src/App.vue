<script setup>
  import { ref, onMounted, computed } from 'vue';

  const pokemons = ref([]);
  const filterText = ref('');

  const filteredPokemon = computed(() => {
    return pokemons.value.filter((pokemon) => {
      return pokemon.name.includes(filterText.value);
    });
  });

  onMounted(async () => {
    const data = await fetch(
      'https://pokeapi.co/api/v2/pokemon?limit=151&offset=0'
    ).then((response) => response.json());

    pokemons.value = data.results;
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
  <button
    type="button"
    class="card-container"
    v-for="pokemon in filteredPokemon"
  >
    <img
      class="image-poke"
      v-bind:src="
        'https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/' +
        (pokemons.indexOf(pokemon)+1) +
        '.png'
      "
    />
    <div class="footer-card">
      <p>
        {{ pokemon.name[0].toUpperCase()  + pokemon.name.substring(1) }}
      </p>
      <p>#{{ pokemons.indexOf(pokemon)+1 }}</p>
    </div>
  </button>
  <p class="signature">Desenvolvido pela mestre pokémon: Lili Gouveia</p>
</template>

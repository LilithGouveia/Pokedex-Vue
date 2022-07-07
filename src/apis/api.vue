<script>
  import Card from '../Components/Card.vue'
  export default {
    name: "getPokemon",
    data() {
        return {
            pokemons: null,
        };
    },
    mounted() {
        fetch("https://pokeapi.co/api/v2/pokemon?limit=151&offset=0")
            .then((response) => response.json())
            .then((data) => (this.pokemons = data.results));
        console.log(this.pokemons);
    },
    components: { Card }
};
</script>

<template>
  <ul>
    <Card v-for="(pokemon, index) in pokemons"
    :key="`poke-${index}`"
    :name="pokemon.name"
    :number="index+1"
    />
  </ul>
</template>

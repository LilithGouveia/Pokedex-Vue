<script>
  import GetPokemon from '../src/apis/api.vue';
  import Card from '../src/Components/Card.vue';
  import Input from './Components/Input.vue';
  export default {
    name: 'app',
    components: {
    GetPokemon,
    Card,
    Input,
},
  };
</script>

<template>
    <Input />
    <GetPokemon />
    <p class="signature">Desenvolvido pela mestre pokémon: Lili Gouveia</p>
</template>

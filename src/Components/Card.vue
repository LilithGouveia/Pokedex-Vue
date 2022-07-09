<script setup>
  import { defineProps, computed } from 'vue';

  const props = defineProps({
    name: {
      type: String,
      required: true,
    },
    number: {
      type: Number,
      required: true,
    },
  })

  const pokeName = computed(() => {
    return props.name[0].toUpperCase()  + props.name.substring(1);
  });
</script>
<template>
<button type="button" class="card-container">
  <img class="image-poke" v-bind:src="'https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/' + number +'.png'" />
  <div class="footer-card">
    <p>
      {{ pokeName }}
    </p>
    <p>
  #{{ number }}
    </p>
  </div>
</button>
</template>
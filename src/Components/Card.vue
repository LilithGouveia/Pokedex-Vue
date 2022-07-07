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
  <p>
    #{{ number }} - {{ name }}
  </p>
</template>

<style>
/* #app {} */
</style>

<template>
  <h1>{{ title }}</h1>
</template>

<script setup>
import { defineProps } from 'vue'

defineProps({
  title: String
})

</script>

<style scoped>

  h1 {
    font-size: 3.16rem;    
    font-weight: bold;
  }

</style>
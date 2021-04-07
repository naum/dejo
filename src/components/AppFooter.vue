<template>
  <footer>
    {{ copyrightMessage }}
  </footer>
</template>

<script setup>
import { defineProps } from 'vue'

defineProps({
  copyrightMessage: String
})

</script>

<style scoped>

  footer {
    color: #D6ECF0;
    font-size: 0.75rem;    
    font-style: italic;
  }

</style>
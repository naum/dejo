<template>
  <div>
    <p>{{ message }}</p>
    <h3>{{ league.name }}</h3>
    <button @click="state.count += 1">Count is: {{ state.count }}</button>
    <button @click="$emit('changename')">Call Parent</button>
    <button @click="pingDaddy($event)">Ping Parent</button>
  </div>
</template>

<script setup>
import { inject, defineEmit, defineProps, reactive } from 'vue'

const prop = defineProps({
  message: String,
  maxteamOpt: Array
})

const emit = defineEmit(['changename', 'ping'])

const state = reactive({
  count: 0
})

const league = inject('uba')
console.log('league: ' + league)
console.log('league keys ' + Object.keys(league))
console.log('league.name: ' + league.name)
league.name = "New UBA"
console.log('league.name: ' + league.name)
league.teams.push('Pittsburgh')

const pingDaddy = (e) => {
  console.log("Love. Love. Love.")
  emit('ping')
}

console.log('prop from setup: ' + prop.message)
console.log('prop from setup 2: ' + prop.maxteamOpt)

const showProp = () => {
  console.log('prop.message: ' + prop.message)
}
</script>

<style scoped>
  button {
    border-radius: 4rem;
    font-family: monospace;
    font-size: 1.33rem;
    font-weight: bold;
    padding: 0.33rem 0.75rem;
  }

  div {
    min-height: 32rem;
  }
</style>
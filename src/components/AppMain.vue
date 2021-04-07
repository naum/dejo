<template>
  <div>
    <p>{{ message }}</p>
    <h3>{{ league.name }}</h3>
    <button @click="state.count += 1">Count is: {{ state.count }}</button>
    <button @click="$emit('changename')">Call Parent</button>
    <button @click="pingDaddy($event)">Ping Parent</button>
    <button @click="genesis()">Genesis</button>
    <div>
      <li v-for="team in league.teams" :key="team">
        {{ team }}
      </li>
    </div>
  </div>
</template>

<script setup>
import { inject, defineEmit, defineProps, reactive } from 'vue'
import usaCities from '../../usaCities.json'

const prop = defineProps({
  message: String,
  maxteamOpt: Array
})

const emit = defineEmit(['changename', 'ping'])

const state = reactive({
  count: 0
})

const league = inject('uba')
league.name = "UBA Redux"
league.teams = usaCities.cities

const pingDaddy = (e) => {
  emit('ping')
}

console.log('prop from setup: ' + prop.message)
console.log('prop from setup 2: ' + prop.maxteamOpt)

const genesis = () => {
  league.teams = shuffle(league.teams)
}

const showProp = () => {
  console.log('prop.message: ' + prop.message)
}

const shuffle = (array) => {
    let counter = array.length;
    while (counter > 0) {
        let index = Math.floor(Math.random() * counter);
        counter--;
        let temp = array[counter];
        array[counter] = array[index];
        array[index] = temp;
    }
    return array;
}

</script>

<style scoped>
  button {
    background-color: #85C6D4;
    color: #172D31;
    border-radius: 0.25rem;
    font-family: monospace;
    font-weight: bold;
    padding: 0.33rem 0.75rem;
  }

  button:hover {
    background-color: #AED9E3;
  }

  div {
    margin-top: 1rem;
    min-height: 32rem;
  }

  h3 {
    font-family: monospace;
  }

  li {
    list-style: none;
  }
</style>
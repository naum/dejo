<template>
  <AppHeader title="dejo" />
  <AppMain 
    message="a simple counter" 
    @changename="hi()"
    @ping="hiAgain()"
    :maxteamOpt="[8,20,32]"
  />
  <AppFooter
    copyright-message="A GNT creation &copy;2021"
  />
</template>

<script setup>
import AppHeader from './components/AppHeader.vue'
import AppFooter from './components/AppFooter.vue'
import AppMain from './components/AppMain.vue'

import { provide, reactive } from 'vue'

const uba = reactive({
  ballplayers: [],
  name: 'UBA',
  teams: [],
  season: 0
})

const hi = () => {
  console.log('changing league name')
  uba.name = 'New and Improved UBA'
  console.log('Total teams: ' + uba.teams.length)
}

const hiAgain = () => {
  console.log("here we are again.")
}

provide('uba', uba)

</script>

<style>
/* BASE COLOR: #5CB2C5 */
#app {
  font-family: monospace;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  font-size: 133.33%;
  line-height: 1.33rem;
  text-align: center;
  color: #172D31;
  margin-top: 3rem;
}
</style>
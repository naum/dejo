<template>
  <AppHeader title="dejo" />
  <AppMain 
    message="a simple counter and id generator" 
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
  uba.name = rollRandString()
}

const hiAgain = () => {
  console.log("here we are again.")
}

const rollRandString = () => {
  const x = Math.random()
  return x.toString(36).slice(-8).toUpperCase()
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
  margin-top: 3rem;
}
</style>
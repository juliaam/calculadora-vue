<template>
  <NavBar />
    <CalculadoraMain />
</template>

<script>

import NavBar from './components/NavBar.vue';
import CalculadoraMain from './components/CalculadoraMain.vue'


export default {
  name: 'App',
  components: {
    NavBar,
    CalculadoraMain
  },
}
</script>

<style>

body {
  background-color: aquamarine;
  font-family: 'Courier New', Courier, monospace;
  font: bold;
  margin: 0;
}
</style>

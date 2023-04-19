aqui vai ficar o que vai aparecer em todas as telas, este lugar é soberano!!

<template>
  <NavBar :logo="logo" :alt="alt"/>
    <DashBoard/>
    <CalculadoraMain/>
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
  data() {
    return {
      logo:"/icons/logo.png",  
      alt: "Calculadora Vue",
    }
  },
  methods: {
    
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

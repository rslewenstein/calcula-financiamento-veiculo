<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
  <Calcula msg="Simulador de Financiamento Veicular"/>
</template>

<script>
import Calcula from './components/Calcula.vue'

export default {
  name: 'App',
  components: {
    Calcula
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

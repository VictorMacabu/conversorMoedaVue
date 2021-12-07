<template>  
  <div id="app">
    <h1>Conversor de Moedas</h1>
      <Conversor moeda1="{{selected1}}" moeda2="{{selected2}}"/>
  </div>
</template>

<script>
import Conversor from "./components/Conversor.vue"

export default {
  name: 'App',
  components: {
    Conversor
  }
}
</script>

<style>
body{
  text-align: center;
  background-color: blueviolet;
}
h1{
  color: #fff;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  display: inline-flex;
  flex-direction: column;
  align-items: center;
}
</style>

<template>
  <div id="app">
    <Calculator />
  </div>
</template>

<script setup>
import Calculator from "./components/Calculator.vue";
</script>

<style>
h1 {
  justify-content: center;
  text-align: center;
  display: flex;
}
#app {
  text-align: center;
  display: flex;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
}
</style>

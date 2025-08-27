<script setup>
import QuoteComponent from './components/QuoteComponent.vue';

</script>

<template>
  <div id="app" :style="{backgroundColor: '#f0f0f0'}">
    <QuoteComponent /> 
  </div>
</template>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>

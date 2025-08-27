<script setup>
import QuoteComponent from './components/QuoteComponent.vue';
import { ref } from 'vue';

const colors = ["#B71C1C", "#880E4F", "#4A148C", "#311B92", "#1A237E", "#0D47A1", "#01579B", "#006064", "#004D40", "#1B5E20", "#33691E", "#827717", "#F57F17", "#FF6F00", "#E65100", "#BF360C"]
const currentColor = ref(colors[Math.floor(Math.random() * colors.length)])

function getRandomColor() {
  currentColor.value = colors[Math.floor(Math.random() * colors.length)];
}

console.log(import.meta.env.VITE_API_KEY)
</script>

<template>
  <div id="app" :style="{backgroundColor: currentColor}">
    <QuoteComponent @colorChange="getRandomColor" :currentColor="currentColor" /> 
  </div>
</template>

<style>

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  display: flex;
  justify-content: center;
  align-items: center;

  width: 100%;
  height: 100vh;

  transition: backgroundColor 0.3s ease;
}
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>

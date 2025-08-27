<script setup>
import { ref } from 'vue';
const colors = ['#FFCDD2', '#F8BBD0', '#E1BEE7', '#D1C4E9', '#C5CAE9', '#BBDEFB', '#B3E5FC', '#B2EBF2', '#B2DFDB', '#C8E6C9', '#DCEDC8', '#F0F4C3', '#FFF9C4', '#FFECB3', '#FFE0B2', '#FFCCBC'];
const currentColor = ref(colors[Math.floor(Math.random() * colors.length)])
function getRandomColor() {
  currentColor.value = colors[Math.floor(Math.random() * colors.length)];
}
</script>
<template>
  <div class="quote-component">
    <blockquote :style="{color: currentColor}">
      <p> The only limit to our realization of tomorrow is our doubts of today.</p>
      <footer>- Franklin D. Roosevelt</footer>
      <button @click="getRandomColor">Change Color</button>
    </blockquote>
  </div>
</template>
<style scoped>
.quote-component {
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 10px;
}
blockquote p {
  margin: 0;
  margin-bottom: 1rem;
}
blockquote p::before {
  content: "\201C";
}
blockquote p::after {
  content: "\201D";
}
</style>

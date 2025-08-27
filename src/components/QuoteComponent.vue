<script setup>
import { ref, defineEmits } from 'vue';
const emit = defineEmits(['colorChange']);
const colors = ['#FFCDD2', '#F8BBD0', '#E1BEE7', '#D1C4E9', '#C5CAE9', '#BBDEFB', '#B3E5FC', '#B2EBF2', '#B2DFDB', '#C8E6C9', '#DCEDC8', '#F0F4C3', '#FFF9C4', '#FFECB3', '#FFE0B2', '#FFCCBC'];
const currentColor = ref(colors[Math.floor(Math.random() * colors.length)])
function getRandomColor() {
  currentColor.value = colors[Math.floor(Math.random() * colors.length)];
}
function newQuote() {
  getRandomColor();
  emit('colorChange', currentColor.value);
}
</script>
<template>
  <div class="quote-component">
    <blockquote :style="{color: currentColor}">
      <p> The only limit to our realization of tomorrow is our doubts of today.</p>
      <footer>- Franklin D. Roosevelt</footer>
      <button :style="{backgroundColor: currentColor}" @click="newQuote">Change Color</button>
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
blockquote {
  display: flex;
  flex-direction: column;
  align-items: flex-start;

  padding: 1.5rem;
  max-width: 600px;
}
blockquote p {
  margin: 0;
  margin-bottom: 1rem;

  transition: color 0.3s ease;
}
blockquote p::before {
  content: "\201C";
}
blockquote p::after {
  content: "\201D";
}
blockquote button {
  align-self: flex-end;
  
  border: none;
  color: white;

  padding: 0.5rem 1rem;
  margin-top: 1rem;

  border-radius: 5px;
  cursor: pointer;

  transition: background-color 0.3s ease;
}
</style>

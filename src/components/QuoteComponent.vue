<script setup>
import { ref } from 'vue';
import quotes from '../quotes.json';
const emit = defineEmits(['colorChange']);

defineProps({currentColor: String})

const quote = ref({quote: "The only limit to our realization of tomorrow is our doubts of today.", author: "Franklin D. Roosevelt"})

async function newQuote() {
  const randomIndex = Math.floor(Math.random() * quotes.length);
  quote.value = quotes[randomIndex];
  emit('colorChange');
}
</script>

<template>
  <div class="quote-component">
    <blockquote :style="{color: currentColor}">
      <p>{{ quote.quote }}</p>
      <footer>- {{ quote.author }}</footer>
      <button :style="{backgroundColor: currentColor}" @click="newQuote">New quote</button>
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
  background-color: white;

  border-radius: 8px;
}
blockquote p {
  margin: 0;
  margin-bottom: 1rem;

  transition: color 0.5s ease;
}
blockquote p::before {
  content: "\201C";
}
blockquote p::after {
  content: "\201D";
}
blockquote footer {
  align-self: flex-end;
  font-style: italic;

  transition: color 0.5s ease;
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

<script setup>
import { ref } from 'vue';
import axios from 'axios';
const emit = defineEmits(['colorChange']);

defineProps({currentColor: String})

const quote = ref({quote: "The only limit to our realization of tomorrow is our doubts of today.", author: "Franklin D. Roosevelt"})

async function newQuote() {
  await axios.get("https://api.api-ninjas.com/v1/quotes",
    {
     headers: {
        "X-API-KEY": `${import.meta.env.VITE_API_KEY}`
      }
    }).then((response) => quote.value = response.data[0])
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

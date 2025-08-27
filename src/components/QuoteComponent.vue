<script setup>

</script>
<template>
  <div class="quote-component">
    <blockquote>
      The only limit to our realization of tomorrow is our doubts of today.
      <footer>- Franklin D. Roosevelt</footer>
    </blockquote>
  </div>
</template>
<style scoped>
blockquote p::before {
  content: "\201C";
}
blockquote p::after {
  content: "\201D";
}
</style>

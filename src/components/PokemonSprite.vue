<script setup>
defineProps(["src"])
</script>

<template>
  <img v-if="src" :src="src" alt="">
  <div v-else class="skeleton"></div>
</template>

<style scoped>
img {
  max-width: 17.5rem;
}

.skeleton {
  background-color: #3b3b3b;

  width: 17.5rem;
  aspect-ratio: 1 / 1;

  border-radius: 1.25rem;

  animation-name: loading;
  animation-duration: 2s;
  animation-iteration-count: infinite;
  animation-timing-function: ease-in-out;
}

@keyframes loading {
  0% {
    opacity: 1;
  }

  50% {
    opacity: .5;
  }

  100% {
    opacity: 1;
  }
}
</style>
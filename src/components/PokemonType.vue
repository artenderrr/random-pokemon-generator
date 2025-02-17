<script setup>
defineProps(["src"])
</script>

<template>
  <img v-if="src" :src="src">
  <div v-else class="skeleton"></div>
</template>

<style>
img {
  max-width: 8.5rem;
}

.skeleton {
  background-color: #3b3b3b;

  height: 2rem;
  aspect-ratio: 4.25 / 1;

  border-radius: .75rem;

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
<template>
  <p v-if="$slots.default">
    <slot />
  </p>
  <div v-else class="skeleton"></div>
</template>

<style scoped>
p {
  color: #6b6b6b;

  font-size: 3rem;
}

.skeleton {
  background-color: #3b3b3b;

  height: 3.5rem;
  aspect-ratio: 5 / 1;

  border-radius: 1rem;

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
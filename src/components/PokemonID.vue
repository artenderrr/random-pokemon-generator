<template>
  <p v-if="$slots.default">
    № <slot />
  </p>
  <div v-else class="skeleton"></div>
</template>

<style scoped>
p {
  color: #6b6b6b;
}

.skeleton {
  background-color: #3b3b3b;

  height: 2.5rem;
  aspect-ratio: 2.5 / 1;

  border-radius: .5rem;

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
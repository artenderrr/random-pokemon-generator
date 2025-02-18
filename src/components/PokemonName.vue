<script setup>
import { ref, onUpdated, useSlots } from "vue";

const slots = useSlots();

const fontSize = ref(3);

onUpdated(() => {
  if (slots.default()[0].children) {
    const pokemonNameLength = slots.default()[0].children.length;
    if (pokemonNameLength > 10 && pokemonNameLength < 15) {
      fontSize.value = 2.5;
    } else if (pokemonNameLength > 14 && pokemonNameLength < 20) {
      fontSize.value = 2;
    } else if (pokemonNameLength > 20) {
      fontSize.value = 1.5;
    } else {
      fontSize.value = 3;
    }
  } 
})
</script>

<template>
  <p v-if="!!$slots.default()[0].children" :style="{ fontSize: fontSize + 'rem' }">
    <slot />
  </p>
  <div v-else class="skeleton"></div>
</template>

<style scoped>
p {
  color: #cdcdcd;

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
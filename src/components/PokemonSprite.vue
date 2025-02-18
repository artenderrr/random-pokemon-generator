<script setup>
import { ref, watch } from "vue";

const props = defineProps(["src"]);

const loadedSrc = ref(null);

watch(() => props.src, (newSrc) => {
  if (!newSrc) {
    loadedSrc.value = null;
  } else {
    const img = new Image();
    img.src = props.src;
    img.onload = () => {
      loadedSrc.value = props.src;
    };
  }
});
</script>

<template>
  <img v-if="loadedSrc" :src="loadedSrc">
  <div v-else class="skeleton"></div>
</template>

<style scoped>
img {
  max-width: 17.5rem;
  min-height: 17.5rem;
}

.skeleton {
  background-color: #3b3b3b;

  width: 17.5rem;
  height: 17.5rem;

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
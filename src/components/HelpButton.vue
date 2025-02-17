<template>
  <button>?</button>
</template>

<style scoped>
button {
  background-color: #202020;
  color: #3b3b3b;

  font: inherit;

  width: 3rem;
  aspect-ratio: 1 / 1;

  border: .125rem solid #3b3b3b;
  border-radius: 50%;

  cursor: pointer;

  transition: filter .25s, transform .125s;
}

button:hover {
  filter: brightness(1.1);
}

button:active {
  transform: scale(.925);
}
</style>
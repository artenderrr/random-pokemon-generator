<template>
  <button>
    <svg class="pokeball" xmlns="http://www.w3.org/2000/svg" width="200" height="200" viewBox="0 0 24 24">
      <g fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2">
        <path d="M3 12a9 9 0 1 0 18 0a9 9 0 1 0-18 0"/>
        <path d="M9 12a3 3 0 1 0 6 0a3 3 0 1 0-6 0m-6 0h6m6 0h6"/>
      </g>
    </svg>
  </button>
</template>

<style scoped>
button {
  background-color: #202020;

  width: 10rem;
  height: 6rem;
  aspect-ratio: 1 / 1;

  display: flex;
  justify-content: center;
  align-items: center;

  border: .125rem solid #3b3b3b;
  border-radius: 1.5rem;

  cursor: pointer;

  transition: filter .25s, transform .125s;
}

button:hover {
  filter: brightness(1.1);
}

button:active {
  transform: scale(.925);
}

.pokeball {
  color: #3b3b3b;
  
  width: 5rem;
  height: 5rem;
}
</style>
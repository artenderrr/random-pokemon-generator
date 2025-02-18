<template>
  <div class="modal-background"></div>
  <div class="modal-window">
    <p>
      Press on
      <svg class="pokeball-icon" xmlns="http://www.w3.org/2000/svg" width="200" height="200" viewBox="0 0 24 24"><g fill="none" stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"><path d="M3 12a9 9 0 1 0 18 0a9 9 0 1 0-18 0"/><path d="M9 12a3 3 0 1 0 6 0a3 3 0 1 0-6 0m-6 0h6m6 0h6"/></g></svg>
      to generate random Pokemon!
    </p>
    <button>Got it!</button>
  </div>
</template>

<style scoped>
.modal-background {
  position: absolute;

  background-color: #151515;
  opacity: .75;

  width: 100%;
  height: 100%;
}

.modal-window {
  position: absolute;

  background-color: #202020;

  width: 27.5rem;
  height: 15rem;

  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 1rem;

  border: .125rem solid #3b3b3b;
  border-radius: 1.5rem;

  padding: 2rem;
}

p {
  text-align: center;
}

.pokeball-icon {
  color: #6b6b6b;

  width: 2.5rem;
  height: 2.5rem;

  margin-bottom: -0.6rem;
}

button {
  background-color: #6b6b6b;
  color: #cdcdcd;

  font: inherit;

  border: none;
  border-radius: 1rem;

  padding: .5rem;
  padding-inline: 1.25rem;

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
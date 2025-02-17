<script setup>
import PokemonID from "./PokemonID.vue";

const pokemonData = {
  id: 923,
  name: "Pikcahu",
  sprite: "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/official-artwork/25.png",
  types: [
    "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/types/generation-ix/scarlet-violet/13.png"
  ]
}
</script>

<template>
  <div class="card">
    <PokemonID></PokemonID>
  </div>
</template>

<style>
.card {
  background-color: #202020;

  width: 25rem;
  height: 35rem;

  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;

  border: .125rem solid #3b3b3b;
  border-radius: 1.5rem;
}
</style>
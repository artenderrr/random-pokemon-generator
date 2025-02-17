<script setup>
import PokemonID from "./PokemonID.vue";
import PokemonSprite from "./PokemonSprite.vue";
import PokemonName from "./PokemonName.vue";

const pokemonData = {
  id: 25,
  name: "Pikachu",
  sprite: "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/official-artwork/25.png",
  types: [
    "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/types/generation-ix/scarlet-violet/13.png"
  ]
}
</script>

<template>
  <div class="card">
    <PokemonID>{{ pokemonData.id }}</PokemonID>
    <PokemonSprite :src="pokemonData.sprite"/>
    <PokemonName>{{ pokemonData.name }}</PokemonName>
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
  gap: 1rem;

  border: .125rem solid #3b3b3b;
  border-radius: 1.5rem;
}
</style>
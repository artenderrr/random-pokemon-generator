<script setup>
import PokemonID from "./PokemonID.vue";
import PokemonSprite from "./PokemonSprite.vue";
import PokemonName from "./PokemonName.vue";
import PokemonType from "./PokemonType.vue";

defineProps(["pokemon", "visible"])
</script>

<template>
  <div v-if="visible" class="card">
    <PokemonID>{{ pokemon.id }}</PokemonID>
    <PokemonSprite :src="pokemon.sprite"/>
    <PokemonName>{{ pokemon.name }}</PokemonName>
    <PokemonType v-for="type in pokemon.types" :src="type"></PokemonType>
  </div>
</template>

<style>
.card {
  background-color: #202020;

  width: 25rem;
  height: 37.5rem;

  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 1rem;

  border: .125rem solid #3b3b3b;
  border-radius: 1.5rem;

  padding: 2rem;
}
</style>
<script setup>
import { ref } from "vue";
import PokeballButton from "./components/PokeballButton.vue";
import HelpButton from "./components/HelpButton.vue";
import PokemonCard from "./components/PokemonCard.vue";

const pokemon = ref(null);

function resetPokemon () {
  pokemon.value = {
    id: null,
    name: null,
    sprite: null,
    types: [null, null]
  };
}

function getRandomPokemonID() {
  return Math.floor(Math.random() * 1025) + 1;
}

async function fetchTypes(typeRefs) {
  const types = await Promise.all(typeRefs.map(async (typeRef) => {
    const response = await fetch(typeRef.type.url);
    const data = await response.json();
    return data.sprites["generation-ix"]["scarlet-violet"]["name_icon"]
  }));
  return types;
}

async function fetchRandomPokemon() { // refactor later
  resetPokemon();

  const id = getRandomPokemonID();

  const response = await fetch(`https://pokeapi.co/api/v2/pokemon/${id}`);
  const data = await response.json();

  const { 
    name,
    sprites: { other: { "official-artwork": { front_default } } },
    types: typeRefs
   } = data;
  const types = await fetchTypes(typeRefs);

  pokemon.value = { id, name: name[0].toUpperCase() + name.slice(1), sprite: front_default, types };
}

resetPokemon();
</script>

<template>
  <HelpButton />
  <PokemonCard :pokemon="pokemon" />
  <PokeballButton @click="fetchRandomPokemon" />
</template>
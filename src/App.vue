<script setup>
import { ref } from "vue";
import PokeballButton from "./components/PokeballButton.vue";
import HelpButton from "./components/HelpButton.vue";
import PokemonCard from "./components/PokemonCard.vue";

const pokemonData = ref(null);

async function fetchTypes(typeRefs) {
  const types = await Promise.all(typeRefs.map(async (typeRef) => {
    const response = await fetch(typeRef.type.url);
    const data = await response.json();
    return data.sprites["generation-ix"]["scarlet-violet"]["name_icon"]
  }));
  return types;
}

async function fetchRandomPokemonData() {
  const randomPokemonID = Math.floor(Math.random() * 1025) + 1;

  const response = await fetch(`https://pokeapi.co/api/v2/pokemon/${randomPokemonID}`);
  const data = await response.json();

  const { 
    name,
    sprites: { other: { "official-artwork": { front_default } } },
    types: typeRefs
   } = data;
  
  const types = await fetchTypes(typeRefs);

  pokemonData.value = { id: randomPokemonID, name, sprite: front_default, types };
}
</script>

<template>
  <HelpButton />
  <PokemonCard />
  <PokeballButton @click="fetchRandomPokemonData" />
</template>
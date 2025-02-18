<script setup>
import { ref } from "vue";
import PokeballButton from "./components/PokeballButton.vue";
import HelpButton from "./components/HelpButton.vue";
import PokemonCard from "./components/PokemonCard.vue";
import HelpModal from "./components/HelpModal.vue";

const pokemon = ref(null);
const pokemonCardVisible = ref(false);
const showModal = ref(false);

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

async function fetchPokemonData(pokemonId) {
  const response = await fetch(`https://pokeapi.co/api/v2/pokemon/${pokemonId}`);
  const data = await response.json();

  const { 
    name,
    sprites: { other: { "official-artwork": { front_default } } },
    types: typeRefs
   } = data;
  const types = await fetchTypes(typeRefs);

  return {
    id: pokemonId,
    name: name[0].toUpperCase() + name.slice(1),
    sprite: front_default,
    types
  };
}

async function getRandomPokemon() {
  resetPokemon();

  const id = getRandomPokemonID();
  const pokemonData = await fetchPokemonData(id);

  pokemon.value = pokemonData;
}

resetPokemon();
</script>

<template>
  <HelpButton @click="showModal = true;"/>
  <PokemonCard :pokemon="pokemon" :visible="pokemonCardVisible" />
  <PokeballButton @click="pokemonCardVisible = true; getRandomPokemon();" />

  <HelpModal v-if="showModal" @hide-modal="showModal = false;"/>
</template>
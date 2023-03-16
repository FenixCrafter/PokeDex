<template>
<header>
  <div class="headerTitle">
    <img src="./assets/pokedex.png" alt=" ">
    <h1>PokeDex</h1>
  </div>
</header>
  <main class="pokeMain">
    <PokeList />
  </main>
</template>

<style scoped>


</style>
<script setup>
import PokeList from "@/vieuws/PokeList.vue";
</script>
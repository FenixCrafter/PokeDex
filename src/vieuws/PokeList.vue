<template>
  <div v-if="pokeData != null" class="pokeList">
    <div v-for="pokemon in pokeData">
      <div v-if="pokemon.url.split('/')[6] < 10263">
        <PokeCard :pokemon-name="pokemon.name" :pokemon-url="pokemon.url" :pokemon-id="pokemon.url.split('/')[6]"/>
      </div>
    </div>
  </div>

  <footer>
    <img src="/src/assets/arrow-left.png" alt="Vorige" @click="setPageIndex(pageIndex+= -1)">
    <input v-model="pageIndex" @change="getPokemonData" type="number" max="60">
    <img src="/src/assets/arrow-right.png" @click="setPageIndex(pageIndex+= 1)" alt="Volgende">
  </footer>
</template>
<script>
import PokeCard from "@/components/PokeCard.vue";

export default {
  components: {PokeCard},
  data() {
    return {
      url_base: "https://pokeapi.co/api/v2/pokemon/",
      pokeData: "",
      pageIndex: 1,
      pageLimit: 21
    }
  },
  methods: {
    getPokemonData() {
      let currentOffset = this.pageLimit * this.pageIndex - this.pageLimit;
      fetch(this.url_base + "?offset=" + currentOffset + "&limit=" + this.pageLimit)
          .then(response => response.json())
          .then(data => {
            this.pokeData = data.results;
            this.goToTop();
          });
    },
    setPageIndex(pageIndex) {
      this.pageIndex = pageIndex;
      if (pageIndex > 0) {
        return this.getPokemonData();
      }

    },
    goToTop() {
      window.scrollTo(0, 0);
    }
  },
  mounted() {
    this.getPokemonData();
  }
}
</script>

<style scoped>
footer {
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
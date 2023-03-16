<style scoped src="/src/assets/css/style.css"></style>

<template>
  <div class="pokeCard">
    <img :src="getPicture()" alt="">
    <h3>{{ pokemonId }}. {{pokemonName}}</h3>
  </div>
</template>
<script>
export default {
  props: {
    pokemonName: {
      type: String,
      required: true
    },
    pokemonUrl: {
      type: String,
      required: true
    },
    pokemonId: {
      type: String,
      required: true
    }
  },
  methods: {
    getPicture(){
      return `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/official-artwork/${this.pokemonUrl.split('/')[6]}.png`
    },
  },
  mounted() {
    this.getPicture();
  }

}

</script>

<style scoped>

</style>
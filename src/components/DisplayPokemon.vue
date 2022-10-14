<template>
  <div>
    <div v-for="(pokemon, index) in pokemons" :key="index">
      <h2>{{ pokemon[1] }}</h2>
      <img :src="pokemon[3]" />
      <p>{{ pokemon[2] }}</p>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      pokemons: [],
    };
  },

  mounted() {
    axios
      .request({
        url: `${process.env.VUE_APP_BASE_DOMAIN}/api/pokemon`,
      })
      .then((response) => {
        this.pokemons = response[`data`];
      })
      .catch((error) => {
        error;
      });
  },
};
</script>

<style lang="scss" scoped>
</style>
<template lang="pug">
#Axios
  h1 {{ "Axios Page" }}
  button(@click="GetPokeInfo" v-if="pokemonData") {{ "Get Sprites" }}
  p {{ pokemonData.name }}
</template>

<script>
export default {
  data() {
    return {
      pokemonData: {},
    };
  },
  methods: {
    async GetPokeInfo() {
      let res = await this.$axios
        .get("https://pokeapi.co/api/v2/pokemon/groudon")
        .then((res) => {
          console.log(res.data);
          this.pokemonData = res.data;
        })
        .catch((err) => {
          return err;
        });
    },
  },
};
</script>
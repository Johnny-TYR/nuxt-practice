<template lang="pug">
#Axios
  h1.title {{ "Axios Practice" }}
  .main-content
    button.btn(v-if="!pokemonData" @click="GetPokeInfo") {{ "Capture Pokemon" }}
    .pokemonCard(v-else)
      img(v-show="false" :src="pokemonData.sprites.front_shiny")
      p {{ pokemonData.name }}
      p {{ pokemonData.sprites.back_default }}
    //-   pre(v-for="item of pokemonData.moves") {{ item.move.name }}



    // 因為我要按按紐才會開始抓資料，所以一開始渲染沒有資料就爆掉了，但為什麼 name 沒爆，因為瀏覽器本身只能抓到第一層，
    // 再下去一層會爆掉
    // 2 ways to render when data is not grabbed yet
    //-   pre {{ pokemonData?.sprites?.back_default}} or v-if 等東西都渲染完才顯示
 
</template>

<script>
export default {
  data() {
    return {
      // don't set as empty object, because it's truthy
      pokemonData: null,
    };
  },
  methods: {
    async GetPokeInfo() {
      let res = await this.$axios
        .get("https://pokeapi.co/api/v2/pokemon/1")
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

<style lang="scss" scoped>
#Axios {
  .title {
    text-align: center;
    color: darkcyan;
    font-size: 50px;
    margin-top: 40px;
  }
  .main-content {
    background-color: tomato;
    // width: 600px;
    // height: 600px;
    position: relative;
    .btn {
      position: absolute;
      top: 50%;
      left: 50%;
    }
  }
}
</style>
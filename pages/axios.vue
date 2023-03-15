<template lang="pug">
#Axios
  h1.title {{ "Axios Practice" }}
  button.btn(@click="GetPokeInfo") {{ "Get Sprite Url" }}
  .showLink
    .pokemonCard(v-if="pokemonData")
      p {{ pokemonData.sprites.front_shiny }}
      img(v-for="", :src="pokemonData.sprites.front_shiny")
    //-   pre(v-for="item of pokemonData.moves") {{ item.move.name }}
  .main-content
    .shinySprites
      .spriteBox(v-for="index in 107", :key="index")
        img.img(:src="GetShinySprites(index + 386)")
        //- span.span {{ `# ${index + 386}` }}
  .problems
    h1.q-title {{ "遇到的問題！" }}
    .text {{ notes.one }}
    .text {{ notes.two }}
    .solve {{ solutions.one }}
    .solve {{ solutions.two }}
</template>

<script>
export default {
  data() {
    return {
      // don't set as empty object, because it's truthy
      pokemonData: null,
      // for getting shiny sprites
      spriteUrl:"https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/shiny/",
      // for setting notes text
      notes: {
        one: "1. 我們抓回來的資料要先在 data() 設變數，再將 axios 抓回來的資料用 this.dataName 存入才能使用",
        two: "2. 因為我們是在按下 btn 才抓資料，所以一開始在還沒抓到資料的情況下渲染，畫面會爆掉。",
      },
      solutions: {
        one: "解決辦法 1：pokemonData?.sprites?.back_default → 在 . 前面加問號",
        two: "解決辦法 2：v-if 等東西都抓到了才顯示 → 記得空物件是 truthy",
      },
    };
  },
  methods: {
    async GetPokeInfo() {
      let res = await this.$axios
        .get(`https://pokeapi.co/api/v2/pokemon/groudon`)
        .then((res) => {
          console.log(res.data);
          this.pokemonData = res.data;
        })
        .catch((err) => {
          return err;
        });
    },
    GetShinySprites(index) {
      return `${this.spriteUrl}${index}.png`;
    },
  },
};
</script>

<style lang="scss" scoped>
* {
  padding: 0;
  margin: 0;
}
#Axios {
  // background: black;
  .title {
    text-align: center;
    color: darkcyan;
    font-size: 50px;
    margin-top: 40px;
  }
  .showLink {
    margin: auto;
    margin-top: 50px;
    background-color: tomato;
    border-radius: 10px;
    width: 700px;
    position: relative;
  }
  .main-content {
    .shinySprites {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      max-width: 700px;
      margin: auto;
      // outline: auto;
      .spriteBox {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        width: 120px;
        height: 120px;
        background-color: white;
        border: 5px double tomato;
        margin: 10px;
        border-radius: 50%;
        img {
          object-fit: contain;
          width: 100%;
        }
      }
    }
  }
  .problems {
    margin: auto;
    background-color: darkcyan;
    max-width: 700px;
    border-radius: 10px;
    color: white;
    padding: 40px 30px;
    margin-top: 50px;
    margin-bottom: 50px;
    .text {
      margin-top: 20px;
    }
    .solve {
      background-color: black;
      margin-top: 30px;
      border-radius: 10px;
      padding: 15px;
    }
  }
}
</style>
<template lang="pug">
#CollapseComponent
  .panel
    .title(@click="ToggleCollapse") {{ "皮卡丘" }}
    .content(:class="{ hide: !isShow }") {{ "This Pokemon is a psychic-type Pokemon " }}
  .panel
    .title {{ "水箭龜" }}
    .content {{ "This Pokemon is a fire-type Pokemon " }}
  .panel
    .title {{ "水箭龜" }}
    .content {{ "This Pokemon is a bug-type pokemon This Pokemon is a bug-type pokemonThis Pokemon is a bug-type pokemonThis Pokemon is a bug-type pokemonThis Pokemon is a bug-type pokemonThis Pokemon is a bug-type pokemon" }}
</template>

<script>
export default {
  data() {
    return {
      isShow: false,
    };
  },
  methods: {
    ToggleCollapse() {
      this.isShow = !this.isShow;
    },
  },
};
</script>

<style lang="scss" scoped>
#CollapseComponent {
  outline: auto;
  display: inline-flex;
  flex-direction: column;

  .panel {
    display: flex;
    flex-direction: column;
    min-width: 500px;
    max-width: 700px;
    .title {
      background-color: lightgray;
      padding: 10px 15px;
      &::before {
        content: "\25BE";
        margin-right: 20px;
        margin-left: 10px;
      }
      &.clicked {
        &::before {
          content: "\25BE";
          margin-right: 20px;
          margin-left: 10px;
          background: yellow;
        }
      }
    }
    .content {
      background: white;
      padding: 25px;
      word-wrap: normal;
      transition: all 0.5s ease-in-out;
    }
  }
  .hide {
    height: 0;
    padding: 0 25px !important;
  }
}
</style>
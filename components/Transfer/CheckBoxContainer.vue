<template lang="pug">
#CheckBoxContainer
  .container
    .srcHeader
      input(type="checkbox", ref="selectAll")
      .header {{ "原列表" }}
    .srcContent
      .content-container
        CheckBox(v-for="pokemon of fakeDataList", :key="pokemon.id", name="checkboxes") {{ pokemon.name }} - {{ pokemon.id }}
</template>

<script>
export default {
  name: "CheckBoxContainer",
  components: {
    CheckBox: () => import("@/components/Transfer/CheckBox.vue"),
  },
  props: {
    fakeDataList: {
      type: Array,
      default: () => [],
    },
  },
};
</script>

<style lang="scss" scoped>
// 排版
#CheckBoxContainer {
  display: flex;
  .container {
    display: grid;
    grid-template-rows: minmax(40p, auto) minmax(50px, auto);
    grid-template-areas:
      "Header"
      "Content";
    overflow: scroll;
    min-width: 100px;
    .srcHeader {
      grid-area: Header;
      background-color: lightblue;
    }
    .srcContent {
      grid-area: Content;
      background-color: darkcyan;
    }
    .targetHeader {
      grid-area: Header;
      background-color: tomato;
    }
    .targetContent {
      grid-area: Content;
      background-color: darkred;
    }
  }
}
</style>
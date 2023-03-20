<template lang="pug">
#CheckBoxContainer
  .container
    .srcHeader
      input(
        type="checkbox",
        ref="selectAllCheck",
        @change="checkAll",
        v-model="allIsChecked"
      )
      .header {{ "原列表" }}
    .srcContent
      .content-container
        CheckBox(
          v-for="pokemon of fakeDataList",
          :key="pokemon.id",
          v-model="checkList",
          :checkBoxData="pokemon"
        ) {{ pokemon.name }} - {{ pokemon.id }}
  pre {{ checkList }}
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
    // disabled: {
    //   type: Boolean,
    //   default: false,
    // },
  },
  data() {
    return {
      allIsChecked: false,
      checkList: [],
    };
  },
  mounted() {
    // console.dir(this.$refs.selectAllCheck)
    console.log();
  },
  methods: {
    checkAll() {
      if (this.allIsChecked) {
        this.checkList.push(...this.fakeDataList);
        this.checkList = [...new Set(this.checkList)];
        return;
      }
      this.checkList = [];
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
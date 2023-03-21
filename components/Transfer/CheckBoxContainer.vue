<template lang="pug">
#CheckBoxContainer
  .container
    .srcHeader
      input(type="checkbox", @change="SelectAll", v-model="isChecked")
      .header
        slot(name="title")
    .srcContent
      .content-container
        CheckBox(
          v-for="pokemon of fakeDataList",
          :key="pokemon.id",
          :checkBoxData="pokemon",
          v-model="checkList"
        ) {{ pokemon.name }} - {{ pokemon.id }}
  p {{ "打勾勾" }}
  pre {{ checkList }}
</template>

<script>
export default {
  name: "CheckBoxContainer",
  components: {
    CheckBox: () => import("@/components/Transfer/CheckBox.vue"),
  },
  props: {
    // 從父層帶進來的
    fakeDataList: {
      type: Array,
      default: () => [],
    },
  },
  data() {
    return {
      // 用來判斷header的框框有沒有勾
      isChecked: false,
      // 因爲要選擇 checkbox 需要每個 checkbox 的 id
      checkList: [],
    };
  },
  methods: {
    SelectAll() {
      if (this.isChecked) {
        // 如果 isChecked，就把 fakeDataList 的資料丟進 checkList
        this.checkList.push(...this.fakeDataList);
        // 為了不讓 array 裡面有重複的值，使用 new Set
        this.checkList = [...new Set(this.checkList)];
        return;
      }
      // 清空 array
      this.checkList = [];
    },
    ClearCheckList() {
      this.checkList = [];
    },
    ClearTargetCheckList() {
      this.targetCheckedIdList = [];
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
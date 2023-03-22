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
          :v-model="checkList"
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
    // 從父層帶進來的主要資料
    fakeDataList: {
      type: Array,
      default: () => [],
    },
  },
  data() {
    return {
      isChecked: false, // 用來判斷header的框框有沒有勾
      checkList: [], // 這個陣列用來裝所有被勾選的資料
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
  },
};
</script>

<style lang="scss" scoped>
// 排版
#CheckBoxContainer {
  border: 1px solid black;
  border-radius: 5px;
  width: 200px;
  height: 230px;
  .container {
    display: grid;
    grid-template-rows: 50px minmax(260px 1fr);
    grid-template-areas:
      "Header"
      "Content";
    .srcHeader {
      grid-area: Header;
      display: flex;
      align-items: center;
      background-color: cyan;
      border-top-right-radius: 5px;
      border-top-left-radius: 5px;
      border-bottom: 1px solid black;
      padding: 10px 12px;
      input[type="checkbox"] {
        margin-right: 12px;
        width: 15px;
        height: 15px;
      }
    }
    .srcContent {
      grid-area: Content;
      // background-color: lightblue;
      background-color: #fff;
      border-bottom-left-radius: 5px;
      border-bottom-right-radius: 5px;
      padding: 0 12px;
      height: 180px;
      overflow: auto;
    }
  }
}
.center {
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
<template lang="pug">
#Transfer
  .containerBox
    CheckBoxContainer(
      ref="CheckBoxContainerLeft",
      :fakeDataList="fakeDataList"
    )
      p(slot="title") {{ "源列表" }}
    .gap
      button.arrow.arrow-icon(@click="ClickSend") {{ ">" }}
      button.arrow.arrow-icon(@click="ClickBack") {{ "<" }}
    CheckBoxContainer(
      ref="CheckBoxContainerRight",
      :fakeDataList="newDataList"
    )
      p(slot="title") {{ "目的列表" }}
</template> 

<script>
export default {
  components: {
    CheckBoxContainer: () =>
      import("@/components/Transfer/CheckBoxContainer.vue"),
  },
  props: {
    fakeDataList: {
      type: Array,
      default: () => [],
    },
    newDataList: {
      type: Array,
      default: () => [],
    },
  },
  methods: {
    ClickSend() {
      // 這裡抓的是 CheckBoxContainer 的 computed
      const checkList = this.$refs.CheckBoxContainerLeft.checkList;
      // console.log(this.newDataList, checkList);
      this.DeleteArraySelected(this.fakeDataList, checkList);
      this.newDataList.push(...checkList);
      // this.$refs.CheckBoxContainerLeft.checkList = [];
      this.ClearCheckList();
    },
    ClickBack() {
      // 這裡抓的是 CheckBoxContainer 的 computed
      const checkList = this.$refs.CheckBoxContainerRight.checkList;
      // console.log(this.newDataList, checkList);
      this.DeleteArraySelected(this.newDataList, checkList);
      this.fakeDataList.push(...checkList);
      this.ClearCheckList();
    },
    DeleteArraySelected(originArr, selectedArr) {
      for (const selectItem of selectedArr) {
        const { id } = selectItem;
        const _findIndex = originArr.findIndex((item) => item.id === id);
        if (_findIndex > -1) {
          originArr.splice(_findIndex, 1);
        }
      }
    },
    ClearCheckList() {
      this.$refs.CheckBoxContainerLeft.checkList = [];
      this.$refs.CheckBoxContainerRight.checkList = [];
    },
  },
};
</script>

<style lang="scss" scoped>
// 排版
#Transfer {
  .containerBox {
    display: flex;
    // ** gap styles =======================
    .gap {
      // background: red;
      min-width: 50px;
      @extend .center;
      flex-direction: column;
      .arrow {
        padding: 5px 10px;
        margin-bottom: 10px;
        color: darkgray;
        border: 1px solid darkgray;
        border-radius: 3px;
      }
      .arrow-icon {
        user-select: none;
      }
    }
  }
}
// universal CSS
.center {
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
<template lang="pug">
#Transfer
  .containerBox
    // left side
    CheckBoxContainer(
      ref="CheckBoxContainerLeft",
      :fakeDataList="fakeDataList"
    )
      p(slot="title") {{ "源列表" }}
    // gap
    .gap
      button.arrow.arrow-icon(@click="ClickSend") {{ "▶" }}
      button.arrow.arrow-icon(@click="ClickBack") {{ "◀" }}
    // right side
    CheckBoxContainer(
      ref="CheckBoxContainerRight",
      :fakeDataList="newDataList"
    )
      p(slot="title") {{ "目的列表" }}
    // only for data showing
    p {{"原本的"}}
    pre {{  fakeDataList }}
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
  },
  data() {
    return {
      newDataList: [],
    };
  },
  mounted() {
    // console.log(this.fakeDataList);
  },
  methods: {
    ClickSend() {
      const _checkedIdList = this.$refs.CheckBoxContainerLeft.checkedIdList; // 這裡抓的是 CheckBoxContainer 的 computed
      this.newDataList.push(..._checkedIdList);
      this.newDataList = [...new Set(this.newDataList)];
      this.$refs.CheckBoxContainerLeft.ClearCheckList();
      this.$emit("on-change", this.newDataList);
      console.log("right btn clicked", _checkedIdList);
      console.log(this.newDataList);
    },
    ClickBack() {
      console.log("go to left side");
      // this.fakeDataList.push({ name: "aaa", id: 5 });
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
      background: red;
      min-width: 50px;
      @extend .center;
      flex-direction: column;
      .arrow-icon {
        user-select: none;
      }
    }
  }
}

// 元件
#Transfer {
}

// universal CSS
.center {
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
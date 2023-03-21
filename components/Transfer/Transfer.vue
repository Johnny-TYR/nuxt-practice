<template lang="pug">
#Transfer
  .containerBox
    CheckBoxContainer(
      ref="CheckBoxContainerLeft",
      :fakeDataList="fakeDataList"
    )
    .gap
      button.arrow.arrow-icon(@click="ClickSend") {{ "▶" }}
      button.arrow.arrow-icon(@click="ClickBack") {{ "◀" }}
    CheckBoxContainer(
      ref="CheckBoxContainerRight",
      :fakeDataList="fakeDataList"
    )

    pre {{ fakeDataList }}
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
  computed: {
    newDataList() {
      return this.fakeDataList.map((obj) => {
        return obj.id;
      });
    },
  },
  mounted() {
    console.log(this.fakeDataList);
  },
  methods: {
    ClickSend() {
      const checkedIdList = this.$refs.CheckBoxContainerLeft.checkedIdList;
      console.log(checkedIdList);
    },
    ClickBack() {
      console.log("go to left side");
      this.fakeDataList.push({ name: "aaa", id: 5 });
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
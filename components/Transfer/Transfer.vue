<template lang="pug">
#Transfer
  .containerBox
    CheckBoxContainer(:fakeDataList = "fakeDataList")
    .gap
      .arrow.arrow-icon(@click="send") {{ "▶" }}
      .arrow.arrow-icon(@click="back") {{ "◀" }}
    CheckBoxContainer(:fakeDataList = "fakeDataList")
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
  mounted() {
    console.log(this.fakeDataList);
  },
  methods: {
    send() {
      console.log("go to right side");
    },
    back() {
      console.log("go to left side");
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
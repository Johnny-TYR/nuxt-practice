<template lang="pug">
#ButtonsComponent
  .btn(:class="btnClass", @click="HandleClick")
    slot
</template>

<script>
export default {
  props: {
    type: {
      type: String,
      default: "default",
    },
    disabled: {
      type: Boolean,
      default: false,
    },
  },
  methods: {
    HandleClick() {
      console.log("clicked");
    },
  },
  computed: {
    btnClass() {
      const btnClassList = [`btn-${this.type}`];
      if (this.disabled) {
        btnClassList.push("btn-disabled");
      }
      return btnClassList;
      4;
    },
  },
};
</script>

<style lang="scss" scoped>
// 排版
#ButtonsComponent {
  display: flex;
}
// 樣式
#ButtonsComponent {
  .btn {
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 10px 30px;
    border-radius: 5px;
  }
  .btn-default {
    border: 1px solid black;
  }
  .btn-disabled {
    background: yellow;
  }
}
</style>
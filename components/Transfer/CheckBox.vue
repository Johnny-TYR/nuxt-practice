<template lang="pug">
#CheckBox
  .checkbox
    input(
      type="checkbox",
      @change="EmitValue",
      :value="checkBoxData",
      v-model="checkList"
    )
    slot
  pre {{checkBoxData}}
</template>

<script>
export default {
  name: "CheckBox",
  props: {
    vvv: {
      type: Array,
      default: () => [],
    },
    checkBoxData: {
      type: Object,
      default: () => ({}),
    },
  },
  data() {
    return {
      checkList: this.vvv,
    };
  },
  watch: {
    vvv() {
      this.checkList = this.vvv;
    },
  },
  methods: {
    EmitValue() {
      this.$emit("update", this.checkList);
    },
  },
};
</script>

<style lang="scss" scoped>
#CheckBox {
  .checkbox {
    display: flex;
    align-items: center;
  }
}
</style>
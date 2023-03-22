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
</template>

<script>
export default {
  name: "CheckBox",
  props: {
    value: {
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
      checkList: this.value,
    };
  },
  watch: {
    value() {
      this.checkList = this.value;
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
  margin-top: 20px;
  .checkbox {
    display: flex;
    align-items: center;
    font-size: 1em;
    input[type="checkbox"] {
      margin-right: 12px;
      width: 15px;
      height: 15px;
    }
  }
}
</style>
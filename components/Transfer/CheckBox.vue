<template lang="pug">
#CheckBox
  .checkbox
    input(type="checkbox", @change="EmitValue", :value="checkBoxData" v-model="checkList")
    slot
  //- pre {{checkBoxData}}
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
      this.$emit("input", this.checkList);
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
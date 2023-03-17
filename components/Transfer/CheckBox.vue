<template lang="pug">
#CheckBox
  .checkbox
    input(type="checkbox")
    slot
</template>

<style lang="scss" scoped>
#CheckBox {
  .checkbox {
    display: flex;
    align-items: center;
  }
}
</style>
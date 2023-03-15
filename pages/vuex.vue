<template lang="pug">
#Vuex
  h1.title {{ "Vuex Practice Page" }}
</template>

<style lang="scss" scoped>
#Vuex {
  .title {
    text-align: center;
    color: darkcyan;
    font-size: 50px;
    margin-top: 25px;
    &::before {
      content: "✨";
      display: inline-flex;
      justify-content: center;
      align-items: center;
      width: 55px;
      height: 55px;
      background-color: darkcyan;
      border-radius: 50%;
      padding: 10px;
      margin-right: 10px;
    }
  }
}
</style>
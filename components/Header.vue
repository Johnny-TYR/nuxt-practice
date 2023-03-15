<template lang="pug">
#Header
  .navbar
    Nuxt-link.Nuxt-link(to="/") {{ "Home Page" }}
    Nuxt-link.Nuxt-link(to="/vuex") {{ "Vuex Practice" }}
    Nuxt-link.Nuxt-link(to="/grid") {{ "Grid Practice" }}
</template>

<style lang="scss" scoped>
#Header {
  .navbar {
    background: lightblue;
    display: flex;
    justify-content: center;
    .Nuxt-link {
      box-sizing: border-box;
      border-radius: 10px;
      text-decoration: none;
      font-weight: bold;
      color: black;
      padding: 10px 20px;
      border: 3px double black;
      margin: 20px;
      &:hover{
        background-color: darkcyan;
        color: white;
        border: 3px double white;
      }
    }
  }
}
</style>
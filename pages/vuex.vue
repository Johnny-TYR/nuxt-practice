<template lang="pug">
#Vuex
  h1.title {{ "Vuex Practice Page" }}
  .article
    .nav
      .vuexLinks
        Nuxt-link.nuxt-link(to="/vuex") {{ "Read Me" }}
        Nuxt-link.nuxt-link(to="/vuex/nuxtVuex") {{ "Nuxt Vuex" }}
    .main
      nuxt-child
</template>

<style lang="scss" scoped>
#Vuex {
  .title {
    text-align: center;
    color: darkcyan;
    font-size: 50px;
    margin-top: 40px;
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
  .article {
    max-width: 1000px;
    // outline: auto;
    margin: auto;
    margin-top: 30px;
    display: flex;
    flex-direction: column;
    .nav {
      .vuexLinks {
        display: flex;
        justify-content: center;
        .nuxt-link {
          padding: 10px 20px;
          border-radius: 5px;
          background-color: darkcyan;
          display: inline-block;
          margin: 10px 20px ;
          text-decoration: none;
          color: white;
          min-width: 6rem;
          text-align: center;
        }
      }
    }
    .main {
      margin-top: 20px;
      background-color: #454545;
      border-radius: 10px;
      padding: 50px;
    }
  }
}
</style>
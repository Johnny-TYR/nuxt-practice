<template lang="pug">
#ComponentsPractice
  h1.title {{ "All Different Components" }}
  .navbar
    Nuxt-link.navlink(to="/componentsPractice/collapse") {{ "Collapse 折疊面板" }}
    Nuxt-link.navlink(to="/componentsPractice/buttons") {{ "Buttons 按紐" }}
  .main
    nuxt-child
</template>
<script>
export default {
  components: {
    collapse: () => import("@/components/Collapse.vue"),
  },
};
</script>

<style lang="scss" scoped>
#ComponentsPractice {
    .navbar{
        background-color: black;
        .navlink{
            text-decoration: none;
            color: white;
            margin-right: 50px;
        }
    }
}
</style>
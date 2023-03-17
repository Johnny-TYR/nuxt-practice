<template lang="pug">
#ComponentsPractice
  .navbar
    Nuxt-link.navlink(to="/componentsPractice/buttons") {{ "Buttons 按紐" }}
    Nuxt-link.navlink(to="/componentsPractice/collapse") {{ "Collapse 折疊面板" }}
    Nuxt-link.navlink(to="/componentsPractice/transfer") {{ "Transfer 穿梭匡" }}
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
        margin-bottom: 20px;
        padding: 20px;
        .navlink{
            text-decoration: none;
            color: white;
            margin-right: 50px;
        }
    }
}
</style>
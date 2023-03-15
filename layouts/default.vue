<template lang="pug">
#Layouts
  Header
  Nuxt
</template>

<script>
export default {
  components: {
    Header:()=>import("@/components/Header.vue"),
  },
};
</script>
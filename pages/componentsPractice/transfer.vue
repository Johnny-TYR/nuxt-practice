<template lang="pug">
#TransferPage
  Transfer(:fakeDataList="fakeDataList")
</template>

<script>
export default {
  components: {
    Transfer: () => import("@/components/Transfer/Transfer.vue"),
  },
  data() {
    return {
      fakeDataList: [
        { name: "Pikachu", id: 1 },
        { name: "Chimchar", id: 2 },
        { name: "Turtwig", id: 3 },
        { name: "Piplup", id: 4 },
      ],
    };
  },
};
</script>
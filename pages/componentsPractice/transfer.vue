<template lang="pug">
#TransferPage
  Transfer(:fakeDataList="fakeDataList", @on-change="ChangeFakeDataList")
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
  methods: {
    ChangeFakeDataList(arr) {
      console.log(arr);
      // let _newArr = [];
      for (const info of arr) {
        this.fakeDataList = this.fakeDataList.filter((item) => item.id !== info.id);
      }
      // console.log(_newArr);
    },
  },
};
</script>
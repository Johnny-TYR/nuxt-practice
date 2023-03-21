<template lang="pug">
#TransferPage
  Transfer(
    :fakeDataList="fakeDataList",
    :newDataList="newDataList",
    @on-change="ChangeFakeDataList"
  )
  //- p {{"Original"}}
  //- pre {{fakeDataList}}
  //- p {{"Transfer"}}
  //- pre {{newDataList}}
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
        { name: "Charmander", id: 5 },
        { name: "Squirtle", id: 6 },
        { name: "Bulbasaur", id: 7 },
        { name: "Pichu", id: 8 },
        { name: "pokemon9", id: 9 },
        { name: "pokemon10", id: 10 },
        { name: "pokemon11", id: 11 },
        { name: "pokemon12", id: 12 },
        { name: "pokemon13", id: 13 },
        { name: "pokemon14", id: 14 },
        { name: "pokemon15", id: 15 },
      ],
      newDataList: [],
    };
  },
  methods: {
    ChangeFakeDataList(arr) {
      console.log(arr);
      // let _newArr = [];
      for (const info of arr) {
        this.fakeDataList = this.fakeDataList.filter(
          (item) => item.id !== info.id
        );
      }
      // console.log(_newArr);
    },
  },
};
</script>
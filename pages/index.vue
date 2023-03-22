<template lang="pug">
#Index
  ToDoList
</template>

<script>
import Vue from "vue";

export default Vue.extend({
  name: "IndexPage",
  components: {
    ToDoList: () => import("@/components/ToDoList/ToDoList.vue"),
  },
});
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>
<style lang="scss" scoped>
#Index {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 91vh;
  background-color:lightgreen;
}
</style>

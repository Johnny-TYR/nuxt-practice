<template lang="pug">
#playground
  input(type="text", v-model="inputData")
  h1 {{ inputData }}
</template>

<script>
export default {
  name: "playground",
  data() {
    return {
      inputData: "Hello World",
    };
  },
};
</script>


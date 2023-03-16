<template lang="pug">
#Collapse
  Collapse
    h1(slot="title") {{ "Fire" }}
    p(slot="content") {{ "Charmander! I choose you!" }}
  Collapse
    h1(slot="title") {{ "Water" }}
    p(slot="content") {{ "Squirtle! I choose you!" }}
  Collapse
    h1(slot="title") {{ "Grass" }}
    p(slot="content") {{ "Bulbasaur! I choose you!" }}
  Collapse
    h1(slot="title") {{ "picture" }}
    img(slot="content" src="https://fontawesomeicons.com/lib/svg/logo-vue.svg") 

  //- Example
  //- CollapseTest
  //-   span(slot="title") {{ "皮卡丘皮卡丘皮卡丘皮卡丘皮卡丘皮卡丘皮卡丘皮卡丘皮卡丘皮卡丘皮卡丘" }}
  //-   span {{ "1\n2\n3" }}
  //- CollapseTest
  //-   span(slot="title") {{"皮卡丘皮卡丘皮卡丘皮卡丘皮卡丘皮卡丘皮卡丘皮卡丘皮卡丘皮卡丘皮卡丘"}}
  //-   span {{"1\n2\n3"}}
  //- CollapseTest
  //-   span(slot="title") {{"皮卡丘皮卡丘皮卡丘皮卡丘皮卡丘皮卡丘皮卡丘皮卡丘皮卡丘皮卡丘皮卡丘"}}
  //-   span {{"1\n2\n3"}}
</template>

<script>
export default {
  components: {
    Collapse: () => import("@/components/Collapse.vue"),
    CollapseTest: () => import("@/components/CollapseTest"),
  },
};
</script>

<style lang="scss" scoped>
#Collapse{
  img{
    object-fit: contain;
    width: 200px;
    height: 200px;
    width: 100%;
  }
} 
</style>

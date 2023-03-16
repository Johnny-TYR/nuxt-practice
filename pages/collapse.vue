<template lang="pug">
#Collapse
  Collapse


  //- Example
  CollapseTest
    span(slot="title") {{"皮卡丘皮卡丘皮卡丘皮卡丘皮卡丘皮卡丘皮卡丘皮卡丘皮卡丘皮卡丘皮卡丘"}}
    span {{"1\n2\n3"}}
  //- CollapseTest
  //-   span(slot="title") {{"皮卡丘皮卡丘皮卡丘皮卡丘皮卡丘皮卡丘皮卡丘皮卡丘皮卡丘皮卡丘皮卡丘"}}
  //-   span {{"1\n2\n3"}}
  //- CollapseTest
  //-   span(slot="title") {{"皮卡丘皮卡丘皮卡丘皮卡丘皮卡丘皮卡丘皮卡丘皮卡丘皮卡丘皮卡丘皮卡丘"}}
  //-   span {{"1\n2\n3"}}
</template>

<script>
export default {
  components:{
    Collapse: ()=>import("@/components/Collapse.vue"),
    CollapseTest: ()=>import("@/components/CollapseTest")
  }
}
</script>

<template lang="pug">
#Collapse
  .arrow-area.arrow-btn {{ "►" }}
  .title-area {{ "This is the title" }}
  .content-area {{ "This is the content" }}
</template>

<style lang="scss" scoped>
// 佈局
#Collapse {
  display: grid;
  grid-template-rows: minmax(45px auto) 1fr;
  grid-template-columns: 45px 1fr;
  grid-template-areas:
    "arrow title"
    "content content ";
  .arrow-area {
    grid-area: arrow;
    background-color: blue;
    @extend .center;
  }
  .title-area {
    grid-area: title;
    background-color: lightslategray;
  }
  .content-area {
    grid-area: content;
    background-color: yellow;
  }
}
.center {
  display: flex;
  justify-content: center;
  align-items: center;
}
// 元件
#Collapse {
}
</style>
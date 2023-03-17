<template lang="pug">
#Transfer
  .containerBox
    .srcContainer
      .srcHeader srcHeader
      .srcContent srcContent
    .gap gap
    .targetContainer
      .targetHeader targetHeader
      .targetContent targetContent
</template> 

<style lang="scss" scoped>
// 排版
#Transfer {
  .containerBox {
    display: flex;
    // ** left container =======================
    .srcContainer {
      outline: auto;
      // ================ delete
      display: grid;
      grid-template-rows: minmax(50px, auto) minmax(100px, auto);
      grid-template-areas:
        "srcHeader"
        "srcContent";
      .srcHeader {
        grid-area: srcHeader;
        background-color: lightblue;
      }
      .srcContent{
        grid-area: srcContent;
        background-color: darkblue;
      }
    }
    // ** middle container =======================
    .gap {
      background: red;
      min-width: 50px;
      // ================ delete
    }
    // ** right container =======================
    .targetContainer {
      outline: auto;
      background: yellow;
      //   min-width: 100px;
      // ================
    }
  }
}
// 佈局
#Transfer {
}
.center {
  display: flex;
  justify-content: center;
  align-items: centers;
}
</style>
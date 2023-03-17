<template lang="pug">
#Transfer
  .containerBox
    .container
      .srcHeader srcHeader
      .srcContent
        .content
          input(type="checkbox")
          content content 1
        .content
          input(type="checkbox")
          content content 1
        .content
          input(type="checkbox")
          content content 1
        .content
          input(type="checkbox")
          content content 1
    .gap gap
    .container
      .targetHeader targetHeader
      .targetContent targetContent
</template> 

<style lang="scss" scoped>
// 排版
#Transfer {
  .containerBox {
    display: flex;
    // ** container style =======================
    .container {
      display: grid;
      grid-template-rows: minmax(40p, auto) minmax(50px, auto);
      grid-template-areas:
        "Header"
        "Content";
      overflow: scroll;
      .srcHeader {
        grid-area: Header;
        background-color: lightblue;
      }
      .srcContent {
        grid-area: Content;
        background-color: darkcyan;
      }
      .targetHeader {
        grid-area: Header;
        background-color: tomato;
      }
      .targetContent {
        grid-area: Content;
        background-color: darkred;
      }
      .content {
        // outline: auto;
        // display: flex;
      }
    }
    // ** middle container =======================
    .gap {
      background: red;
      min-width: 50px;
      // ================ delete
    }
  }
}
// 元件
#Transfer {
}
// 其他
.center {
  display: flex;
  justify-content: center;
  align-items: centers;
}
</style>
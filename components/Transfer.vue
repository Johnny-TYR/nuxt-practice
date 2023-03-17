<template lang="pug">
#Transfer
  .containerBox
    .container
      .srcHeader srcHeader
      .srcContent srcContent
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
      grid-template-rows: minmax(50px, auto) minmax(100px, auto);
      grid-template-areas:
        "Header"
        "Content";
      .srcHeader {
        grid-area: Header;
        background-color: lightblue;
      }
      .srcContent{
        grid-area: Content;
        background-color: darkblue;
      }
      .targetHeader {
        grid-area: Header;
        background-color: tomato;
      }
      .targetContent{
        grid-area: Content;
        background-color: darkred;
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
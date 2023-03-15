<template lang="pug">
#Collapse
  .panel 
    .title {{ "皮卡丘" }}
  .content {{ "This Pokemon is a psychic-type Pokemon " }}
  .panel 
    .title {{ "水箭龜" }}
  .content {{ "This Pokemon is a fire-type Pokemon " }}
  .panel 
    .title {{ "水箭龜" }}
  .content {{ "This Pokemon is a bug-type Pokemon" }}
</template>

<style lang="scss">
#Collapse {
  background-color: white;
  box-sizing: border-box;
  min-width: 500px;
  max-width: 700px;
  display: inline-flex;
  flex-direction: column;
  .panel {
    min-height: 40px;
    background-color: #d3d3d3;
    display: flex;
    justify-content: flex-start;
    align-items: center;
    padding-left: 10px;
    border-bottom: 1px solid darkgray;
    border-right: 1px solid darkgray;
    border-left: 1px solid darkgray;
    &:nth-of-type(1) {
      border-top: 1px solid darkgray;
    }
    // &.clicked .title {
    //   transform: rotate(90deg);
    //   transition: 0.5s ease-in-out;
    //   background-color: yellow;
    // }
    .title {
      &::before {
        content: "\25BE";
        margin-right: 20px;
        margin-left: 10px;
      }
    }
  }
  .content {
    min-height: 60px;
    padding: 30px 20px;
    word-wrap: normal;
    background-color: white;
    border-bottom: 1px solid darkgray;
    border-right: 1px solid darkgray;
    border-left: 1px solid darkgray;
  }
}
</style>
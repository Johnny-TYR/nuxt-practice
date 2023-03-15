<template lang="pug">
#Collapse
  .panel {{ "One" }}
  .content {{ "this is the first panel" }}
  .panel {{ "Two" }}
  .content {{ "this is the second panel" }}
  .panel {{ "Three" }}
  .content {{ "this is the third panel " }}
</template>

<style lang="scss">
#Collapse {
  background-color: white;
  box-sizing: border-box;
  border: 1px solid rgba(0, 0, 0, 0.6);
  min-width: 500px;
  max-width: 100;
  display: inline-flex;
  flex-direction: column;
  .panel {
    min-height: 40px;
    background-color: lightgrey;
    display: flex;
    justify-content: flex-start;
    align-items: center;
    padding-left: 10px;
  }
  .content {
    min-height: 60px;
    padding:5px 10px;
  }
}
</style>
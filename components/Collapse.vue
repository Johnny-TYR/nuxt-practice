<template lang="pug">
#Collapse
  .arrow-area(@click="HandleClick")
    .arrow-btn(:class="{ 'rotate-arrow': isOpen }") {{ "►" }}
  .title-area {{ "This is the title" }}
  .content-area(ref="CollapseContent", :style="contentAreaStyle")
    .content-box {{ dummyText }}
</template>

<script>
export default {
  name: "Collapse",
  data() {
    return {
      isOpen: false,
      dummyText:
        "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.",
    };
  },
  methods: {
    HandleClick() {
      this.isOpen = !this.isOpen;
      console.log("open");
    },
  },
  computed: {
    contentAreaStyle() {
      if (!this.isOpen) return {};
      console.log(this.$refs.CollapseContent);
      const height = this.$refs.CollapseContent.scrollHeight;
      return {
        "max-height": `${height}px`,
      };
    },
  },
};
</script>

<style lang="scss" scoped>
// 佈局
#Collapse {
  display: grid;
  grid-template-rows: minmax(45px auto) 1fr;
  grid-template-columns: 45px 1fr;
  grid-template-areas:
    "arrow title"
    "content content ";
  // top left ============
  .arrow-area {
    grid-area: arrow;
    background-color: lightslategray;
    @extend .center;
    .arrow-btn {
      transition: transform .6s ease-in-out;
    }
  }
  // top right ===========
  .title-area {
    grid-area: title;
    background-color: lightslategrey;
    display: flex;
    align-items: center;
    padding: 10px;
  }
  // bottom row ==========
  .content-area {
    grid-area: content;
    background-color: goldenrod;
    max-height: 0;
    overflow: hidden;
    // text wrap
    word-break: break-all;
    white-space: pre-wrap;
    word-wrap: break-word;
    // transition
    transition: 1s ease-in-out;
    .content-box {
      padding: 10px 20px;
    }
  }
}
// 元件
#Collapse {
  .arrow-btn {
    cursor: pointer;
    user-select: none;
  }
  .rotate-arrow {
    transform: rotate(90deg);
  }
}
// 其他
.center {
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
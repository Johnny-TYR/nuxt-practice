<template lang="pug">
#Collapse
  .title-area(@click="HandleClick")
    .arrow-area
      .arrow-btn(:class="{ 'rotate-arrow': isOpen }") {{ "►" }}
    slot(name="title")
  .content-area(ref="CollapseContent", :style="contentAreaStyle")
    .content-box
      slot(name="content") 
</template>

<script>
export default {
  name: "Collapse",
  props: {
    headerText: {
      type: String,
      default: "title",
    },
    contentText: {
      type: String,
      default: "content",
    }
  },
  data() {
    return {
      isOpen: false,
    };
  },
  methods: {
    HandleClick() {
      this.isOpen = !this.isOpen;
      console.log("toggle");
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
  grid-template-rows: minmax(45px, auto) 1fr;
  grid-template-columns: 45px 1fr;
  grid-template-areas:
    "title title"
    "content content ";
  // top left ============
  .arrow-area {
    grid-area: arrow;
    background-color: #dcdee2;
    @extend .center;
    padding: 0 30px 0 20px;
    // outline: auto;
    .arrow-btn {
      transition: transform 0.2s ease-in-out;
    }
  }
  // top right ===========
  .title-area {
    grid-area: title;
    background-color: #dcdee2;
    display: flex;
    align-items: center;
    padding: 10px;
  }
  // bottom row ==========
  .content-area {
    grid-area: content;
    background-color: #fff;
    max-height: 0;
    overflow: hidden;
    // text wrap
    word-break: break-all;
    white-space: pre-wrap;
    word-wrap: break-word;
    // transition
    transition: 0.2s ease-in-out;
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
<template lang="pug">
#CollapseTest
  .arrow-area.arrow-btn(@click="isOpen=!isOpen")
    .arrow-icon(:class="{'arrow-rotate': isOpen}") {{"►"}}
  .header-area
    slot(name="title")
    
  .content-area(ref="CollapseContent" :style="contentStyle")
    .content-box
      slot
    
</template>

<script>
export default {
  name: "CollapseTest",
  props: {
    headerText: {
      type: String,
      default: "title"
    },
    contentText: {
      type: String,
      default: "content"
    }
  },
  data () {
    return {
      isOpen: false,
    }
  },
  mounted () {
    console.dir(this.$refs.CollapseContent)
  },
  computed: {
    contentStyle () {
      if (!this.isOpen) return {};
      const height = this.$refs.CollapseContent.scrollHeight;
      return {
        "max-height": `${height}px`
      }
    }
  }
}
</script>

<style lang="scss" scoped>
// 佈局
#CollapseTest {
  display: grid;
  grid-template-columns: 40px 1fr;
  grid-template-rows: minmax(40px, auto) 1fr;
  grid-template-areas:
    "arrow header"
    "content content";
  .arrow-area {
    grid-area: arrow;
    background: #eee;
    @extend .center;
  }
  .header-area {
    grid-area: header;
    background: #eee;
    display: flex;
    align-items: center;
    // word-break: break-all;
    // white-space: pre-wrap;
    // word-wrap: break-word;
  }
  .content-area {
    grid-area: content;
    // padding: 10px;
    background: #999;
    max-height: 0;
    overflow: hidden;
    transition: max-height 0.4s ease-in-out;
  }
}
// 元件
#CollapseTest {
  .arrow-btn {
    cursor: pointer;
    user-select: none;
  }
  .arrow-icon {
    transition: transform 0.4s ease;
  }
  .arrow-rotate {
    transform: rotate(90deg);
  }
  .content-box {
    padding: 10px;
  }
}

.center {
  display: flex;
  align-items: center;
  justify-content: center;
}

</style>

<template>
  <div style="height:100%">
    <split-pane
      v-show="!showEdit"
      split="horizontal"
      :min-percent="minPercent"
      :default-percent="defaultPercent"
      @resize="resize"
    >
      <template slot="paneL" orientation="VERTICAL_SPLIT">
        <div class="top-container">
          <div>
            <questions-detail />
            <common-card />
          </div>
        </div>
      </template>
      <template slot="paneR" orientation="VERTICAL_SPLIT" split="horizontal">
        <div ref="element" class="bottom-container">
          <div v-show="!showCommonSimple" class="foot">
            <div class="foot-left mx-2">
              <el-button type="info" class="icon-left" icon="el-icon-message" circle />
            </div>

            <div class="middle">
              <el-input @click.native="showBottom" /></div>
            <el-button class="button-right mx-2" type="primary">changeStatus</el-button>
          </div>
          <common-simple
            v-show="showCommonSimple"
            :button-height="bottomHeight"
            :textarea-height="textareaHeight"
            class="common-simple"
          />
        </div>
      </template>
    </split-pane>
    <questions-edit v-show="showEdit" />
  </div>
</template>

<script>
import QuestionsEdit from './QuestionsEdit'
import QuestionsDetail from './QuestionsDetail'
import CommonSimple from './CommonSimple'
import CommonCard from './CommonCard'
import splitPane from 'vue-splitpane'

export default {
  components: {
    QuestionsEdit,
    QuestionsDetail,
    CommonSimple,
    CommonCard,
    splitPane
  },
  data() {
    return {
      showEdit: false,
      showCommonSimple: false,
      contentHeight: {
        height: window.innerHeight - 95 + 'px'
      },
      bottomHeight: 50,
      textareaHeight: 260,
      minPercent: 94,
      defaultPercent: 94
    }
  },
  mounted() {
    window.onresize = () => {
      return (() => {
        this.contentHeight.height =
          window.innerHeight - 45 - this.bottomHeight + 'px'
      })()
    }
  },
  methods: {
    resize() {
      const height = this.$refs.element.offsetHeight
      var that = this
      that.$data.minPercent = 10
      that.$data.bottomHeight = height - 18 - 56
      that.$data.textareaHeight = height - 18 - 56 - 56
      if (this.$children[0].percent > 53) {
        that.$data.minPercent = 49
      }
    },
    addHeight() {
      this.bottomHeight = 340
    },
    reduceHeight() {
      this.bottomHeight = 50
    },
    questionEdit() {
      this.showEdit = true
    },
    save() {
      this.showEdit = false
    },
    showBottom() {
      this.showCommonSimple = true
      this.addHeight()
      this.$data.minPercent = 10
      this.$data.defaultPercent = 52
    },
    closeCommonSimple() {
      this.showCommonSimple = false
      this.reduceHeight()
      this.$data.minPercent = 94
      this.$data.defaultPercent = 94
    }
  }
}
</script>

<style scoped lang="scss">
.top-container {
  height: 100%;
  overflow: auto;
}
.bottom-container {
  height: 100%;
}

.foot {
  display: flex;
  height: 50px;
  line-height: 50px;
}
.foot {
  .button-right {
    position: relative;
    top: 7px;
    height: 36px;
  }
  .middle {
    width: 100%;
  }
}
</style>

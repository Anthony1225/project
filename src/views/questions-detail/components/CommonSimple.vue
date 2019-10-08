
<template>
  <div class="main-content">
    <div class="top">=</div>
    <div class="main overflow-hidden">
      <div class="content-left mr-3" :style="{lineHeight:buttonHeight+'px'}">
        <el-button type="warning" icon="el-icon-star-off" circle />
      </div>
      <div class="middle-left mr-3">
        <el-input />
        <textarea class="mt-1" :style="{height:textareaHeight+'px'}" />
        <!-- <el-input type="textarea" v-model="form.desc"></el-input> -->
      </div>

      <div v-show="rightDisplay" class="middle-right right mr-2">
        <el-button-group>
          <el-button type="info">Open</el-button>
          <el-button type="info">In Progress</el-button>
          <el-button type="info">Resloved</el-button>
          <el-button type="info">Close</el-button>
        </el-button-group>
        <div class="row">
          <div class="row-left row-child">
            <label for>Assignee</label>
            <el-input />
          </div>
          <div class="row-right row-child">
            <label for>Start Date</label>
            <el-date-picker
              v-model="displayTime"
              style="margin-top:10px;width: 180px;"
              type="datetime"
              format="yyyy-MM-dd HH:mm:ss"
              placeholder="Select date and time"
            />
          </div>
        </div>
        <div class="row">
          <div class="row-left row-child">
            <label for>Milestone</label>
            <el-input />
          </div>
          <div class="row-right row-child">
            <label for>Due date</label>
            <el-date-picker
              v-model="displayTime"
              style="margin-top:10px;width: 180px;"
              type="datetime"
              format="yyyy-MM-dd HH:mm:ss"
              placeholder="Select date and time"
            />
          </div>
        </div>
        <div class="row">
          <div class="row-left row-child">
            <label for>Resolution</label>
            <el-input />
          </div>
          <div class="row-right row-child">
            <label for>Est/Act</label>
            <div>
              <el-input class="row-right-input" />
              <el-input class="row-right-input" />
            </div>
          </div>
        </div>
      </div>
      <div class="rights" :style="{lineHeight:buttonHeight+'px'}">
        <el-button
          v-show="rightDisplay"
          type="warning"
          icon="el-icon-arrow-right"
          circle
          @click="hiddenRight"
        />
        <el-button
          v-show="!rightDisplay"
          type="warning"
          icon="el-icon-arrow-left"
          circle
          @click="showRight"
        />
      </div>
    </div>

    <div class="bottom">
      <el-button type="info" @click="closeCommonSimple">close</el-button>
      <el-button type="success">submit</el-button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    // eslint-disable-next-line vue/require-default-prop
    buttonHeight: {
      type: Number,
      default: 380
    },
    textareaHeight: {
      type: Number,
      default: 260
    }
  },
  data() {
    return {
      rightDisplay: true
    }
  },
  methods: {
    closeCommonSimple() {
      this.$parent.$parent.$parent.closeCommonSimple()
    },
    hiddenRight() {
      this.rightDisplay = false
    },
    showRight() {
      this.rightDisplay = true
    },
    dropBottom() {
      this.$parent.$parent.$parent.dropBottomHeight()
    }
  }
}
</script>

<style scoped lang="scss">
.bottom {
  padding: 10px;
  position: absolute;
  bottom: 0;
  left: 50%;
  margin-left: -56px;
  text-align: center;
}
.main {
  padding: 10px 10px 0px 10px;
  display: flex;
}
.main {
  .middle-right {
    width: 380px;
    flex-shrink: 0;
  }
}

textarea {
  width: 100%;
  padding: 4px 7px;
  border: 1px solid #d9d9d9;
  border-radius: 4px;
}
.row-child {
  width: 44%;
  display: inline-block;
  padding: 10px 0px;
}

.row-left {
  margin-right: 6%;
}
.row-left  .el-input {
  margin: 10px 0px;
}
.row-right-input {
  width: 40%;
}
.row-right-input:nth-child(1) {
  margin-right: 16%;
}
.top {
  text-align: center;
  color: #909399;
}
.middle-left{
  width: 100%;
}
</style>

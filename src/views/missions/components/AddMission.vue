<template>
  <div>
    <div id="drawer-title-div">
      <label>任务追加</label>
      <el-button id="oktoadd-btn">追加</el-button>
    </div>
    <div id="drawer-content-div" :style="contentStyle">
      <el-form label-position="left" label-width="90px" size="medium">
        <el-form-item label="概要">
          <el-input style="width:70%" />
        </el-form-item>
        <el-form-item label="详细">
          <el-input type="textarea" />
        </el-form-item>
        <el-form-item label="担当者">
          <el-select />
        </el-form-item>
        <el-form-item label="预计期间">
          <el-col :span="11">
            <el-date-picker style="width:100%" />
          </el-col>
          <el-col style="text-align:center" :span="2">
            -
          </el-col>
          <el-col :span="11">
            <el-date-picker style="width:100%" />
          </el-col>
        </el-form-item>
        <el-form-item label="预计工时">
          <el-input style="max-width:200px" /><label>&nbsp;&nbsp;人/日</label>
        </el-form-item>
        <el-form-item label="进度率">
          <el-input style="max-width:200px" /><label>&nbsp;&nbsp;%</label>
        </el-form-item>
        <el-form-item label="进度判定">
          <el-select />
        </el-form-item>
      </el-form>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      contentStyle: {
        height: window.innerHeight - 107 + 'px'
      }

    }
  },

  mounted() {
    window.onresize = () => {
      return (() => {
        this.contentStyle.height = window.innerHeight - 32 - 30 - 45 + 'px'
      })()
    }
  }
}
</script>

<style scoped>
.el-col {
  margin-bottom: 0px;
}
#drawer-title-div {
  padding-left: 20px;
  padding-right: 20px;
}
#oktoadd-btn {
  float: right;
}
#drawer-content-div {
  padding-left: 20px;
  padding-right: 20px;
  margin-top: 20px;
  overflow: auto;

}

</style>

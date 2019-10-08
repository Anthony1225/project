<template>
  <div>
    <!-- <div class="pl-4 pr-4">
      <el-button class="right" style="background:green">追加</el-button>
    </div> -->
    <div class="pl-4 pr-4 mt-4" :style="contentStyle">
      <el-form label-position="left" label-width="90px" size="medium">
        <el-row type="flex">
          <el-col span="11">
            <el-form-item label="分类">
              <el-select size="mini" />
            </el-form-item>
          </el-col>
          <el-col span="11">
            <el-form-item label="概要">
              <el-input size="mini" style="width:70%" />
            </el-form-item>
          </el-col>
          <el-button class="right" style="background:green">追加</el-button>
        </el-row>
        <el-form-item label="详细">
          <el-input type="textarea" />
        </el-form-item>
        <el-form-item label="附件">
          <el-upload class="upload-demo" drag action multiple>
            <i class="el-icon-upload" />
            <div class="el-upload__text">
              将文件拖到此处，或
              <em>点击上传</em>
            </div>
            <!-- <div class="el-upload__tip" slot="tip">只能上传jpg/png文件，且不超过500kb</div> -->
          </el-upload>
        </el-form-item>
        <el-form-item label="关联">
          <el-card style="width:360px;margin-bottom:50px" />
        </el-form-item>
        <el-row type="flex">
          <el-col span="12">
            <el-form-item label="担当者">
              <el-select size="mini" />
            </el-form-item>
          </el-col>
          <el-col span="12">
            <el-form-item label="处理状态">
              <el-select size="mini" />
            </el-form-item>
          </el-col>
        </el-row>
        <el-row type="flex">
          <el-col span="12">
            <el-form-item label="重要度">
              <el-select size="mini" />
            </el-form-item>
          </el-col>
          <el-col span="12">
            <el-form-item label="优先度">
              <el-select size="mini" />
            </el-form-item>
          </el-col>
        </el-row>
        <el-row type="flex">
          <el-col span="12">
            <el-form-item label="分类1">
              <el-select size="mini" />
            </el-form-item>
          </el-col>
          <el-col span="12">
            <el-form-item label="分类2">
              <el-select size="mini" />
            </el-form-item>
          </el-col>
        </el-row>
        <el-row type="flex">
          <el-col span="12">
            <el-form-item label="预计开始日">
              <el-date-picker size="mini" />
            </el-form-item>
          </el-col>
          <el-col span="12">
            <el-form-item label="预计结束日">
              <el-date-picker size="mini" />
            </el-form-item>
          </el-col>
        </el-row>
      </el-form>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      contentStyle: {
        height: window.innerHeight - 107 + "px"
      }
    };
  },

  mounted() {
    window.onresize = () => {
      return (() => {
        this.contentStyle.height = window.innerHeight - 32 - 30 - 45 + "px";
      })();
    };
  }
};
</script>

<style scoped>
.el-col {
  margin-bottom: 0px;
  height: 36px;
}
.el-form-item {
  margin-bottom: 5px;
}
label {
  color: #000;
}
.drawer-content-div {
  overflow: auto;
}
</style>

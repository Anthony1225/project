
<template>
  <div class="container">
    <el-row class="column">
      <el-button class="edit right" type="primary" icon="upload" @click="questionEdit">编辑</el-button>
    </el-row>
    <div class="read-content">
      <el-row class="column">
        <el-col :xs="6" :sm="3" :lg="3">
          <label for>分类</label>
        </el-col>
        <el-col :xs="18" :sm="18" :lg="18">
          <label class="content" for>分类内容</label>
        </el-col>
      </el-row>
      <el-row class="column">
        <el-col :xs="6" :sm="3" :lg="3">
          <label for>概要</label>
        </el-col>
        <el-col :xs="18" :sm="18" :lg="18">
          <label class="content" for>概要内容概要内容概要内容概要内容</label>
        </el-col>
      </el-row>
      <el-row class="column">
        <el-col :xs="6" :sm="3" :lg="3">
          <label for>担当着</label>
        </el-col>
        <el-col :xs="18" :sm="18" :lg="18">
          <label class="content" for>小张</label>
        </el-col>
      </el-row>
      <el-row class="column">
        <el-col :xs="6" :sm="3" :lg="3">
          <label for>重要度</label>
        </el-col>
        <el-col :xs="6" :sm="6" :lg="9">
          <label class="content" for>重要</label>
        </el-col>
        <el-col :xs="6" :sm="3" :lg="3">
          <label for>优先度</label>
        </el-col>
        <el-col :xs="6" :sm="6" :lg="9">
          <label class="content" for>一级</label>
        </el-col>
      </el-row>
      <el-row class="column">
        <el-col :xs="6" :sm="3" :lg="3">
          <label for>分类1</label>
        </el-col>
        <el-col :xs="6" :sm="6" :lg="9">
          <label class="content" for>分类1</label>
        </el-col>
        <el-col :xs="6" :sm="3" :lg="3">
          <label for>分类2</label>
        </el-col>
        <el-col :xs="6" :sm="6" :lg="9">
          <label class="content" for>分类2</label>
        </el-col>
      </el-row>
      <el-row class="column">
        <el-col :xs="6" :sm="3" :lg="3">
          <label for>手计开始日</label>
        </el-col>
        <el-col :xs="6" :sm="6" :lg="9">
          <label class="content" for>2019-07-01</label>
        </el-col>
        <el-col :xs="6" :sm="3" :lg="3">
          <label for>手计结束日</label>
        </el-col>
        <el-col :xs="6" :sm="6" :lg="9">
          <label class="content" for>2019-08-01</label>
        </el-col>
      </el-row>
      <el-row class="column">
        <el-col :xs="6" :sm="3" :lg="3">
          <label for>处理状态</label>
        </el-col>
        <el-col :xs="18" :sm="18" :lg="18">
          <label class="content" for>已处理</label>
        </el-col>
      </el-row>
      <el-row class="column-block">
        <el-col :xs="6" :sm="3" :lg="3">
          <label for>详细</label>
        </el-col>
        <el-col :xs="18" :sm="9" :lg="12">
          <el-input type="textarea" :rows="4" />
        </el-col>
      </el-row>
      <el-row class="column-block">
        <el-col :xs="6" :sm="3" :lg="3">
          <label for>附件</label>
        </el-col>
        <el-col :xs="18" :sm="9" :lg="12">
          <el-input type="textarea" :rows="4" />
        </el-col>
      </el-row>
      <el-row class="column-block">
        <el-col :xs="6" :sm="3" :lg="3">
          <label for>关联</label>
        </el-col>
        <el-col :xs="18" :sm="9" :lg="12">
          <el-input type="textarea" :rows="4" />
        </el-col>
      </el-row>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    questionEdit() {
      this.$parent.$parent.$parent.questionEdit()
    }
  }
}
</script>

<style scoped lang="scss">
.edit {
  margin-right: 13px;
}
.container {
  padding: 6px 0px;
}
.el-col {
  line-height: 2;
  margin: 1px 0px;
}

.read-content {
  .column {
    padding: 5px 15px;
    border-bottom: 1px #cccccc solid;
  }
  .column-block {
    padding: 5px 15px;
  }
  .column:nth-child(1) {
    border-top: 1px #cccccc solid;
  }
  .content {
    font-weight: normal;
  }
}
.read-content {
  padding: 5px 30px;
}
textarea {
  resize: none;
}
</style>

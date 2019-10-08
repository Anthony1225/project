
<template>
  <div class="container py-1">
    <el-row class="column">
      <el-button class="save right" type="primary" icon="upload" @click="save">应用</el-button>
    </el-row>
    <div class="edit-content">
      <el-row class="column required">
        <el-col :xs="6" :sm="3" :lg="3">
          <span>*</span>
          <label for>分类</label>
        </el-col>
        <el-col :xs="18" :sm="9" :lg="5">
          <el-select ref="select" v-model="value" placeholder="请选择">
            <el-option
              v-for="item in options"
              :key="item.value"
              :label="item.label"
              :value="item.value"
            />
          </el-select>
        </el-col>
      </el-row>
      <el-row class="column required">
        <el-col :xs="6" :sm="3" :lg="3">
          <span>*</span>
          <label for>概要</label>
        </el-col>
        <el-col :xs="18" :sm="9" :lg="5">
          <el-input />
        </el-col>
      </el-row>
      <el-row class="column">
        <el-col :xs="6" :sm="3" :lg="3">
          <label for>详细</label>
        </el-col>
        <el-col :xs="18" :sm="9" :lg="12">
          <el-input type="textarea" :rows="4" />
        </el-col>
      </el-row>

      <el-row class="column">
        <el-col :xs="6" :sm="3" :lg="3">
          <label for>附件</label>
        </el-col>
        <el-col :xs="18" :sm="9" :lg="12">
          <div class="editor-container">
            <dropzone
              id="myVueDropzone"
              url="https://httpbin.org/post"
              @dropzone-removedFile="dropzoneR"
              @dropzone-success="dropzoneS"
            />
          </div>
        </el-col>
      </el-row>
      <el-row class="column">
        <el-col :xs="6" :sm="3" :lg="3">
          <label for>关联</label>
        </el-col>
        <el-col :xs="18" :sm="9" :lg="12">
          <el-input type="textarea" :rows="4" />
        </el-col>
      </el-row>
      <el-row class="column">
        <el-col :xs="6" :sm="3" :lg="3">
          <label for>担当者</label>
        </el-col>
        <el-col :xs="6" :sm="8" :lg="8">
          <el-input v-model="setSeparator" name="separatorInput" />
        </el-col>
      </el-row>
      <el-row class="column">
        <el-col :xs="6" :sm="3" :lg="3">
          <label for>重要度</label>
        </el-col>
        <el-col :xs="18" :sm="9" :lg="8">
          <el-select ref="select" v-model="value" placeholder="请选择">
            <el-option
              v-for="item in options"
              :key="item.value"
              :label="item.label"
              :value="item.value"
            />
          </el-select>
        </el-col>
        <el-col :xs="6" :sm="3" :lg="3">
          <label for>优先度</label>
        </el-col>
        <el-col :xs="18" :sm="9" :lg="6">
          <el-select ref="select" v-model="value" placeholder="请选择">
            <el-option
              v-for="item in options"
              :key="item.value"
              :label="item.label"
              :value="item.value"
            />
          </el-select>
        </el-col>
      </el-row>
      <el-row class="column">
        <el-col :xs="6" :sm="3" :lg="3">
          <label for>分类1</label>
        </el-col>
        <el-col :xs="18" :sm="9" :lg="8">
          <el-select ref="select" v-model="value" placeholder="请选择">
            <el-option
              v-for="item in options"
              :key="item.value"
              :label="item.label"
              :value="item.value"
            />
          </el-select>
        </el-col>
        <el-col :xs="6" :sm="3" :lg="3">
          <label for>分类2</label>
        </el-col>
        <el-col :xs="18" :sm="9" :lg="8">
          <el-select ref="select" v-model="value" placeholder="请选择">
            <el-option
              v-for="item in options"
              :key="item.value"
              :label="item.label"
              :value="item.value"
            />
          </el-select>
        </el-col>
      </el-row>
      <el-row class="column">
        <el-col :xs="8" :sm="3" :lg="3">
          <label for>手计开始日</label>
        </el-col>
        <el-col :xs="10" :sm="9" :lg="8">
          <el-date-picker
            v-model="displayTime"
            type="datetime"
            format="yyyy-MM-dd HH:mm:ss"
            placeholder="Select date and time"
          />
        </el-col>
        <el-col :xs="8" :sm="3" :lg="3">
          <label for>手计结束日</label>
        </el-col>
        <el-col :xs="10" :sm="9" :lg="8">
          <el-date-picker
            v-model="displayTime"
            type="datetime"
            format="yyyy-MM-dd HH:mm:ss"
            placeholder="Select date and time"
          />
        </el-col>
      </el-row>
      <el-row class="column">
        <el-col :xs="6" :sm="3" :lg="3">
          <label for>处理状态</label>
        </el-col>
        <el-col :xs="18" :sm="9" :lg="8">
          <el-select ref="select" v-model="value" placeholder="请选择">
            <el-option
              v-for="item in options"
              :key="item.value"
              :label="item.label"
              :value="item.value"
            />
          </el-select>
        </el-col>
      </el-row>
    </div>
  </div>
</template>

<script>
import Dropzone from '@/components/Dropzone'

export default {
  components: { Dropzone },
  props: {

  },
  data() {
    return {
      options: [
        { value: '选项1', label: '选项1' },
        { value: '选项2', label: '选项2' },
        { value: '选项3', label: '选项3' },
        { value: '选项4', label: '选项4' }
      ]
    }
  },
  methods: {
    dropzoneS(file) {
      console.log(file)
      this.$message({ message: 'Upload success', type: 'success' })
    },
    dropzoneR(file) {
      console.log(file)
      this.$message({ message: 'Delete success', type: 'success' })
    },
    save() {
      this.$parent.save()
    }
  }
}
</script>

<style scoped lang="scss">
.el-col {
  line-height: 2;
  margin-bottom: 10px;
}
.column {
  padding: 2px 30px;
}
.required span {
  margin-right: 5px;
  color: red;
  position: absolute;
  left: 1%;
}
.column label {
  margin-right: 10px;
}
</style>

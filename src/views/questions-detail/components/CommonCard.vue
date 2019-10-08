
<template>
  <div>
    <el-card v-for="o in 3" :key="o" class="box-card">
      <div slot="header">
        <div>XXXX年XX月XX日</div>
        <div>XX人</div>
        <div>履历来源</div>
        <div>编辑任务</div>
      </div>
      <div class="text item" />
    </el-card>
  </div>
</template>

<script>
export default {}
</script>

<style scoped lang="scss">
.box-card {
  margin: 15px 30px;
}
.box-card div {
  width: 100%;
  display: inline-flex;
}
</style>

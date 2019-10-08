<template>
  <div>
    <el-button @click="drawer=true"><i class="el-icon-plus" /></el-button>
    <el-drawer title="" :visible.sync="drawer" :before-close="handleClose" size="50%">
      <add-mission />
    </el-drawer>
  </div>
</template>

<script>
import AddMission from './components/AddMission'

export default {
  components: { AddMission },
  data() {
    return {
      drawer: false
    }
  },
  methods: {
    handleClose(done) {
      this.$confirm('确认关闭？')
        .then(_ => {
          done()
        })
        .catch(_ => {})
    }
  }
}
</script>

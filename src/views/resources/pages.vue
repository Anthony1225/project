<template>
  <div class="pei">
    <el-select v-model="value" placeholder="请选择" size="small">
      <el-option
        v-for="item in options"
        :key="item.value"
        :label="item.label"
        :value="item.value"
        :disabled="item.disabled"
      ></el-option>
    </el-select>
    <div class="block">
      <!-- <span class="demonstration">默认</span> -->
      <el-date-picker v-model="value1" type="date" placeholder="选择日期"></el-date-picker>
    </div>
    <div class="block">
      <!-- <span class="demonstration">带快捷选项</span> -->
      <el-date-picker
        v-model="value2"
        align="right"
        type="date"
        placeholder="选择日期"
        :picker-options="pickerOptions"
      ></el-date-picker>
    </div>
    <ul class="test" style="float:left;color:white;" v-for="(data,index) in datalist" :key="index">
      <li style="width:30px;height:30px;margin:0 5px;background:blue;">{{data}}</li>
    </ul>
    <!-- <div
        @click="stopHidden"
        class="modal"
        style="width:680px;height:426px;background:yellow;border:1px solid #000;position:fixed;left:50%;top:150px;transform: translateX(-50%);z-index:100"
      >
      <div class="header" style="width:680px;height:50px;background:green;padding:0 20px;font-size:20px;color:white;display:table-cell;vertical-align:middle">View Options<el-button circle size="mini" style="float:right;height:28px;" @click="edit=false"><i class="el-icon-close"/></el-button></div>
      <el-checkbox-group v-model="colOptions">
       	<el-checkbox v-for="item in colSelect" :key="item" :label="item"/>
     </el-checkbox-group>
    </div> -->
    <el-checkbox-group v-model="colOptions" >
    <el-checkbox  :label="list" v-for="list in colSelect" :key="list"></el-checkbox>
    <!-- <el-checkbox label="复选框 A"></el-checkbox>
    <el-checkbox label="复选框 B"></el-checkbox>
    <el-checkbox label="禁用" ></el-checkbox>
    <el-checkbox label="选中且禁用" ></el-checkbox> -->
  </el-checkbox-group>
    </div>
</template>

<script>
export default {
  data() {
    return {
      checkList: ['复选框 A','复选框 B','复选框 C'],
      colOptions:[ '分类', '标题','担当者','完成状态','完成率','计划开始日','计划结束日','计划工时','优先度', '备注','录入者','录入日', '更新者','更新日'],
      colSelect: [ ],
      colData: [
        { title: '分类', istrue: true },
        { title: '标题', istrue: true },
        { title: '担当者', istrue: true },
        { title: '完成状态', istrue: true },
        { title: '完成率', istrue: true },
        { title: '计划开始日', istrue: true },
        { title: '计划结束日', istrue: true },
        { title: '计划工时', istrue: true },
        { title: '优先度', istrue: false },
        { title: '备注', istrue: false },
        { title: '录入者', istrue: false },
        { title: '录入日', istrue: false },
        { title: '更新者', istrue: false },
        { title: '更新日', istrue: false }
      ],
      datalist: [1, 2, 3, 4],
      pickerOptions: {
        disabledDate(time) {
          return time.getTime() > Date.now();
        }
      },
      value1: "",
      value2: "",
      options: [
        {
          value: "选项1",
          label: "黄金糕"
        },
        {
          value: "选项2",
          label: "双皮奶",
          disabled: true
        },
        {
          value: "选项3",
          label: "蚵仔煎"
        },
        {
          value: "选项4",
          label: "龙须面"
        },
        {
          value: "选项5",
          label: "北京烤鸭"
        }
      ],
      value: ""
    };
  },
     mounted(){
       this.colData.filter(i=>{
         if(i.istrue){
           this.colSelect.push(i.title)
         }
    })
     console.log(this.colSelect);
 },

};
</script>
<style>
.pei {
  margin: 0;
  font-size: 1.3rem;
  font-weight: 400;
  font-style: normal;
  line-height: 2rem;
  color: #222;
  background-color: #f0f0f0;
  text-size-adjust: 100%;
}
.pager__link {
  font-size: 1.3rem;
  line-height: 1.8rem;
  padding: 1px 6px 0;
  transition-timing-function: ease-in-out;
  transition-duration: 0.15s;
  transition-property: background-color, color;
  white-space: nowrap;
  color: #222;
  border-radius: 20px;
  outline: none;
  background-color: #fff;
  box-shadow: 0 0 0 1px rgba(0, 0, 0, 0.2);
}

element.style {
}
.pager--numbers .pager__prev {
  padding-right: 8px;
  padding-left: 18px;
}
.pager__link {
  font-size: 1.3rem;
  line-height: 1.8rem;
  padding: 1px 6px 0;
  transition-timing-function: ease-in-out;
  transition-duration: 0.15s;
  transition-property: background-color, color;
  white-space: nowrap;
  color: #222;
  border-radius: 20px;
  outline: none;
  background-color: #fff;
  box-shadow: 0 0 0 1px rgba(0, 0, 0, 0.2);
}
.pager__link,
.pager__partition {
  display: inline-block;
  vertical-align: middle;
}
</style>

<template>
  <div class="question-search pa-4" id="question" @click="edit=false,menu=false,menu1=false">
    <el-button
      @click="control=!control"
      style="color:#1890FF;background:#F5F7FA;border:0;font-weight:600;font-size:16px;position:absolute;top:28px;left:300px;z-index:10 !important"
      size="small"
      :class="control?'el-icon-arrow-up':'el-icon-arrow-down'"
    >
      <!-- <span :class="control?'el-icon-arrow-up':'el-icon-arrow-down'" style="font-size:13px;color:green"> -->
      <!-- </span> -->
    </el-button>
    <el-tabs type="border-card" style="background:#fff;border-radius:0 0 6px 6px;border-color:#c2c2c2">
      <el-tab-pane label="简单搜索">
        <div v-if="control">
          <el-row>
            <el-col :xs="6" :sm="2" :lg="2">
              <label>类型</label>
            </el-col>
            <el-col :xs="18" :sm="9" :lg="8">
              <el-select size="mini" />
            </el-col>
            <el-col :xs="6" :sm="2" :lg="2">
              <label>担当者</label>
            </el-col>
            <el-col :xs="18" :sm="9" :lg="8">
              <el-select size="mini" />
            </el-col>
          </el-row>
          <el-row>
            <el-col :xs="6" :sm="2" :lg="2">
              <label>完成状态</label>
            </el-col>
            <el-col :xs="18" :sm="9" :lg="8">
              <el-select size="mini" />
            </el-col>
          </el-row>
          <el-row>
            <el-col :xs="6" :sm="2" :lg="2">
              <label>关键词</label>
            </el-col>
            <el-col :xs="12" :sm="8" :lg="7">
              <el-input size="mini" />
            </el-col>
            <el-col :xs="4" :sm="14" :lg="15">
              <el-button type="success" style="float:right" size="mini">检索</el-button>
            </el-col>
          </el-row>
        </div>
      </el-tab-pane>
      <el-tab-pane label="高级搜索">
        <div v-if="control">
          <el-row>
            <el-col :xs="6" :sm="2" :lg="2">
              <label>类型</label>
            </el-col>
            <el-col :xs="18" :sm="9" :lg="8">
              <el-select v-model="value4" size="mini" multiple placeholder="请选择">
                <el-option
                  v-for="item in data"
                  :key="item"
                  :label="item"
                  :value="item"
                ></el-option>
              </el-select>
            </el-col>
            <el-col :xs="6" :sm="2" :lg="2">
              <label>担当者</label>
            </el-col>
            <el-col :xs="18" :sm="9" :lg="8">
              <el-select size="mini" v-model="value3" multiple>
                <el-option
                  v-for="item in options1"
                  :key="item.value"
                  :label="item.label"
                  :value="item.value"
                ></el-option>
              </el-select>
            </el-col>
          </el-row>
          <el-row>
            <el-col :xs="6" :sm="2" :lg="2">
              <label>录入者</label>
            </el-col>
            <el-col :xs="18" :sm="9" :lg="8">
              <el-select size="mini" v-model="value" multiple>
                <el-option
                  v-for="item in options"
                  :key="item.value"
                  :label="item.label"
                  :value="item.value"
                ></el-option>
              </el-select>
            </el-col>
            <el-col :xs="6" :sm="2" :lg="2">
              <label>更新者</label>
            </el-col>
            <el-col :xs="18" :sm="9" :lg="8">
              <el-select size="mini" v-model="value5" multiple>
              <el-option
      v-for="item in options2"
      :key="item.value"
      :label="item.label"
      :value="item.value">
    </el-option>
  </el-select>
            </el-col>
          </el-row>
          <el-row>
            <el-col :xs="6" :sm="2" :lg="2">
              <label>计划开始日</label>
            </el-col>
            <el-col :xs="18" :sm="9" :lg="8">
              <div class="block">
                <el-date-picker
                  v-model="value1"
                  style="width:199px"
                  type="date"
                  size="mini"
                  placeholder="选择日期"
                ></el-date-picker>
              </div>
            </el-col>
            <el-col :xs="6" :sm="2" :lg="2">
              <label>计划结束日</label>
            </el-col>
            <el-col :xs="18" :sm="9" :lg="8">
              <div class="block">
                <el-date-picker
                  v-model="value2"
                  style="width:199px"
                  type="date"
                  size="mini"
                  placeholder="选择日期"
                ></el-date-picker>
              </div>
            </el-col>
          </el-row>
          <el-row>
            <el-col :xs="6" :sm="2" :lg="2">
              <label>完成状态</label>
            </el-col>
            <el-col :xs="18" :sm="9" :lg="8">
              <el-select size="mini" />
            </el-col>
            <el-col :xs="6" :sm="2" :lg="2">
              <label>完成率</label>
            </el-col>
            <el-col :xs="18" :sm="9" :lg="8">
              <el-select size="mini" />
            </el-col>
          </el-row>
          <el-row>
            <el-col :xs="6" :sm="2" :lg="2">
              <label>优先度</label>
            </el-col>
            <el-col :xs="18" :sm="9" :lg="8">
              <el-select size="mini" />
              <el-button type="" class="selfbtn" icon="el-icon-question" size="mini" />
              <!-- <el-button class="selfbtn pl-1" icon="el-icon-question" /> -->
            </el-col>
            <el-col :xs="6" :sm="2" :lg="2">
              <label>是否有附件</label>
            </el-col>
            <el-col :xs="18" :sm="9" :lg="8">
              <el-select size="mini" />
              <el-button class="selfbtn" type="" icon="el-icon-question" size="mini" />
            </el-col>
          </el-row>
          <el-row>
            <el-col :xs="6" :sm="2" :lg="2">
              <label>关键词</label>
            </el-col>
            <el-col :xs="12" :sm="8" :lg="7">
              <el-input size="mini" />
            </el-col>
            <el-col :xs="4" :sm="14" :lg="15">
              <el-button type="success" style="float:right" size="mini">检索</el-button>
            </el-col>
          </el-row>
        </div>
      </el-tab-pane>
    </el-tabs>
    <div class="mt-4">
      <div class="" style="line-height:30px">
        <label>检索结果：</label>
        <label style="font-weight:600">XXX件</label>
        <el-pagination
          class="mt-2"
          background
          layout="prev, pager, next"
          :total="20"
          style="display:inline-block;padding:0 60px;margin-top:0 !important;"
        />
        <div class="right menu-modal" style="position:relative;display:inline-block;margin-right:20px">
        <el-button class="right" circle size="mini" style="background:#1890FF" @click="handleMenu">
          <i class="el-icon-more" />
        </el-button>
        <transition name="el-zoom-in-top">
        <ul v-show="menu" class="menu" style="border:1px solid #ccc;width:80px;text-align:center;line-height:30px;cursor: pointer;position:absolute;top:35px;left:-45px;z-index:99;background:#fff">
          <li>导出</li>
          <li @click="handleEdit">编辑</li>
          <li>导入</li>
        </ul>
      </transition>
        </div>
        <el-button class="right" circle size="mini" style="background:#1890FF" @click="getStatus(0)">
          <i class="el-icon-plus" />
        </el-button>
      </div>
      <el-table
        class="result-table mt-2"
        :data="tableData"
        size="mini"
        border
        style="min-width:1200px;border-radius:6px"
      >
        <el-table-column sortable prop="id" label="Id" @click="getStatus(1)">    
          <template slot-scope="scope">
            <el-button type="text" size="mini" @click="getStatus(1)">{{scope.row.id}}</el-button>
          </template>
        </el-table-column>
        <el-table-column sortable v-if="colData[0].istrue" prop="kind" label="分类" />
        <el-table-column sortable v-if="colData[1].istrue" prop="title" label="标题" />
        <el-table-column sortable v-if="colData[2].istrue" prop="person" label="担当者" />
        <el-table-column sortable v-if="colData[3].istrue" prop="completeCondition" label="完成状态" />
        <el-table-column sortable v-if="colData[4].istrue" prop="completePercent" label="完成率" />
        <el-table-column sortable v-if="colData[5].istrue" prop="startDate" label="计划开始日" />
        <el-table-column sortable v-if="colData[6].istrue" prop="endDate" label="计划结束日" />
        <el-table-column sortable v-if="colData[7].istrue" prop="planTime" label="计划工时" />
        <el-table-column sortable v-if="colData[8].istrue" prop="importance" label="优先度" />
        <el-table-column sortable v-if="colData[9].istrue" prop="remarks" label="备注" />
        <el-table-column sortable v-if="colData[10].istrue" prop="creater" label="录入者" />
        <el-table-column sortable v-if="colData[11].istrue" prop="createDate" label="录入日" />
        <el-table-column sortable v-if="colData[12].istrue" prop="updater"  label="更新者" />
        <el-table-column sortable v-if="colData[13].istrue" prop="updateDate"  label="更新日" />
      </el-table>
      <div>
      <el-pagination class="mt-2" background layout="prev, pager, next" :total="100" style="display:inline-block"/>
      <div class="right menu-modal" style="position:relative;display:inline-block;margin-right:20px">
        <el-button class="right" circle size="mini" style="background:#1890FF;margin-top:10px" @click="handleMenu1">
          <i class="el-icon-more" />
        </el-button>
        <transition name="el-zoom-in-top">
        <ul v-show="menu1" class="menu" style="border:1px solid #ccc;width:80px;text-align:center;line-height:30px;cursor:pointer;position:absolute;top:45px;left:-45px;z-index:99;background:#fff">
          <li>导出</li>
          <li @click="handleEdit">编辑</li>
          <li>导入</li>
        </ul>
      </transition>
        </div>
        <el-button class="right" circle size="mini" style="background:#1890FF;margin-top:10px" @click="getStatus(0)">
          <i class="el-icon-plus" />
        </el-button>
        </div>
      <el-drawer
        title="课题追加"
        :visible.sync="drawer"
        :before-close="handleClose"
        size="50%"
        style="background:black;font-weight:600"
      >
        <add-question v-if="sideStatus==0" />
        <edit-question v-if="sideStatus==1" />
      </el-drawer>
      <div
        v-show="edit"
        @click="stopHidden"
        class="modal"
        style="width:680px;height:426px;background:yellow;border:1px solid #000;position:fixed;left:50%;top:150px;transform: translateX(-50%);z-index:100"
      >
      <div class="header" style="width:680px;height:50px;background:green;padding:0 20px;font-size:20px;color:white;display:table-cell;vertical-align:middle">View Options<el-button circle size="mini" style="float:right;height:28px;" @click="edit=false"><i class="el-icon-close"/></el-button></div>
      <el-checkbox-group v-model="colOptions">
        <el-checkbox label="分类" ></el-checkbox>
        <el-checkbox label="标题" ></el-checkbox>
        <el-checkbox label="担当者" ></el-checkbox>
        <el-checkbox label="完成状态" ></el-checkbox>
        <el-checkbox label="完成率" ></el-checkbox>
        <el-checkbox label="计划开始日" ></el-checkbox>
        <el-checkbox label="计划结束日" ></el-checkbox>
        <el-checkbox label="计划工时" ></el-checkbox>
        <el-checkbox label="优先度" ></el-checkbox>
        <el-checkbox label="备注" ></el-checkbox>
        <el-checkbox label="录入者" ></el-checkbox>
        <el-checkbox label="录入日" ></el-checkbox>
        <el-checkbox label="更新者" ></el-checkbox>
        <el-checkbox label="更新日" ></el-checkbox>
     </el-checkbox-group>
    </div>
    </div>
  </div>
</template>
<script>
import AddQuestion from "./components/AddQuestion";
import EditQuestion from "../questions-detail/index";
import { nextTick } from 'q';

export default {
  components: { AddQuestion, EditQuestion },
  watch: {
   colOptions(newVal,oldVal) {
     if (newVal) {   
       var arr = this.colSelect.filter(i => newVal.indexOf(i) < 0) 	
       this.colData.filter(i => {
         if (arr.indexOf(i.title) !== -1) {
           i.istrue = false;
         } else {
           i.istrue = true
         }
       })
     }
   }
 },
  data() {
    return {
      menu: false,
      menu1:false,
      edit:false,
      control: true,
      drawer: false,
      sideStatus: true,
      data:[1,2,3,4],
      value4: "",
      checkList:['复选框 A','复选框 B'],
      colOptions:[ ],
      colSelect: [ '分类', '标题','担当者','完成状态','完成率','计划开始日','计划结束日','计划工时','优先度', '备注','录入者','录入日', '更新者','更新日'],
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
          label: "紧急"
        },
        {
          value: "选项2",
          label: "高"
        },
        {
          value: "选项3",
          label: "中"
        },
        {
          value: "选项4",
          label: "低"
        }
      ],
      value: "",
      options1: [
        {
          value: "选项1",
          label: "重要"
        },
        {
          value: "选项2",
          label: "次要"
        }
      ],
      value3: "",
      options2: [
        {
          value: "选项1",
          label: "张三"
        },
        {
          value: "选项2",
          label: "李四"
        }
      ],
      value5: "",
      tableData: [
        {
          id: "1",
          kind: "过任何反馈举报你的小说了",
          person: "儿童接受任何经济色啊色",
          status: "",
          createDate: "",
          updateDate: "",
          importance: "",
          summary: ""
        },
        {
          id: "22",
          kind: "22222222222",
          person: "环绕声渴望加入天涯",
          status: "",
          createDate: "",
          updateDate: "",
          importance: "",
          summary: ""
        },
        {
          id: "32",
          kind: "33333333333333333333333333333333",
          person: "骄傲u我是占据空间我",
          status: "",
          createDate: "",
          updateDate: "",
          importance: "",
          summary: ""
        },
        {
          id: "100",
          kind: "投入的就准噶尔三个人诱人食欲和",
          person: "天源迪科下面显示得",
          status: "",
          createDate: "",
          updateDate: "",
          importance: "",
          summary: ""
        }
      ]
    };
  },
  mounted(){
        this.colData.filter(i=>{
         if(i.istrue){
           this.colOptions.push(i.title)
         }
    })
  console.log(this.colOptions);
  
  },
  methods: {
    handleClose(done) {
      this.$confirm("确认关闭？")
        .then(_ => {
          done();
        })
        .catch(_ => {});
    },
    getStatus(status) {
      this.sideStatus = status;
      this.drawer = true;
    },
    handleMenu(evt){
      this.menu = !this.menu;
      evt.stopPropagation()
    },
    handleMenu1(evt){
      this.menu1 = !this.menu1;
      evt.stopPropagation()
    },
    handleEdit(evt){
      this.edit = !this.edit;
      evt.stopPropagation();
    },
    stopHidden(evt){
      evt.stopPropagation() 
    }
  }
};
</script>
<style lang='scss'>
#question {
  min-width: 540px;
  min-height: calc(100vh - 50px);
  margin-bottom: 50px;
  .el-tabs--border-card>.el-tabs__content{
    padding: 15px 20px
  }
  .el-col {
    line-height: 2;
    margin-bottom: 3px;
  }
  .el-icon-question {
    font-size: 14px;
  }
  .el-table th {
    // background:turquoise;
  }
  label {
    padding-right: 10px;
    font-weight: 500;
  }
  .selfbtn {
    height: 28px;
    padding: 6px;
  }
  .result-table {
    width: 100%;
    tbody > tr:nth-child(odd){
      background: #FCFADE
    }
  }
  .el-tabs--border-card>.el-tabs__header .el-tabs__item.is-active{
    color: #222
  }
  .el-form-item {
    margin-bottom: 10px;
  }
  .el-pagination button{
    height: 25px
  }
  .el-pager li{
    min-width: 25px;
    height: 25px;
    color:#222 
  }
}
</style>

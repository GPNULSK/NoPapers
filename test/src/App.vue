<template>
  <div id="app">

    <div class="block">
      <span class="demonstration">日期：</span>
      <el-date-picker
        type="date"
        placeholder="选择日期">
      </el-date-picker>
        &nbsp; &nbsp; &nbsp; &nbsp;
      <span class="demonstration">至：</span>
      <el-date-picker
        type="date"
        placeholder="选择日期">
      </el-date-picker>

      &nbsp;&nbsp;&nbsp;&nbsp;
      <span class="demonstration">交送单位：</span>
      <el-select v-model="value" placeholder="请选择">
        <el-option
          v-for="item in options"
          :key="item.value"
          :label="item.label"
          :value="item.value">
        </el-option>
      </el-select>

      <span class="demonstration">分厂人员：</span>
      <el-input style="width: 200px"  placeholder="请输入内容"></el-input>

    </div>
<!--    end div1-->

    <div>
      <br>
      <!--测试中心质量状态下拉框-->
      <span class="demonstration">质量状态：</span>
      <el-select v-model="value" placeholder="请选择">
        <el-option
          v-for="item in options"
          :key="item.value"
          :label="item.label"
          :value="item.value">
        </el-option>
      </el-select>
      <span class="demonstration">当前进度：</span>
      <el-select v-model="value" placeholder="请选择">
        <el-option
          v-for="item in options"
          :key="item.value"
          :label="item.label"
          :value="item.value">
        </el-option>
      </el-select>
      &nbsp;&nbsp;&nbsp;&nbsp;


      <span class="demonstration">物料编码：</span>
      <el-input style="width: 200px"  placeholder="请输入内容"></el-input>
      <span class="demonstration">物料名称：</span>
      <el-input style="width: 200px"  placeholder="请输入内容"></el-input>
    </div>
<!--    end div2-->
    <div>
      <br>
<!--        <span  class="total">总计：1000</span>-->
      <el-button class="btn1" type="primary">查询</el-button>
        <el-button class="btn1" type="primary">出库</el-button>
      <el-button class="btn1" type="primary">入库</el-button>

        <el-button class="btn2" type="primary">导出表格</el-button>
      <br><br>

    </div>



    <template>
      <el-table
        ref="multipleTable"
        :data="tableData"
        tooltip-effect="dark"
        style="width: 100%"
      border>
        <el-table-column
          type="selection"
          width="55">
        </el-table-column>

        <el-table-column
          fixed="left"
          prop=""
          label="查看"
          width="55">
          <template slot-scope="scope">
            <el-button icon="el-icon-search" circle></el-button>
          </template>
        </el-table-column>

        <el-table-column
          prop="status"
          label="当前状态"
          width="60">
        </el-table-column>

        <el-table-column
          prop="name"
          label="交送单位"
          width="80">
        </el-table-column>
        <el-table-column
          prop="address"
          label="分厂人员"
          show-overflow-tooltip>
        </el-table-column>

        <el-table-column
          prop="submittime"
          label="提交时间"
          show-overflow-tooltip>
        </el-table-column>

        <el-table-column
          prop="aps"
          label="APS订单"
          show-overflow-tooltip>
        </el-table-column>

        <el-table-column
          prop="dd"
          label="DD号"
          show-overflow-tooltip>
        </el-table-column>

        <el-table-column
          prop="wlcode"
          label="物料编码"
          show-overflow-tooltip>
        </el-table-column>

        <el-table-column
          prop="wlname"
          label="物料名称"
          show-overflow-tooltip>
        </el-table-column>

        <el-table-column
          prop="khcode"
          label="客户编码"
          show-overflow-tooltip>
        </el-table-column>

        <el-table-column
          prop="khname"
          label="客户名称"
          show-overflow-tooltip>
        </el-table-column>

        <el-table-column
          prop="jssl"
          label="交送数量"
          show-overflow-tooltip>
        </el-table-column>

        <el-table-column
          prop="zjzt"
          label="质量状态"
          show-overflow-tooltip>
        </el-table-column>

        <el-table-column
          prop="bhgyy"
          label="不合格原因"
          show-overflow-tooltip>
        </el-table-column>

        <el-table-column
          prop="time"
          label="质量确认时间"
          show-overflow-tooltip>
        </el-table-column>

        <el-table-column
          prop="renyuan"
          label="质量确认人员"
          show-overflow-tooltip>
        </el-table-column>

        <el-table-column
          prop="wlstatus"
          label="物料状态"
          show-overflow-tooltip>
        </el-table-column>

        <el-table-column
          prop="address"
          label="不合格原因"
          show-overflow-tooltip>
        </el-table-column>


        <el-table-column
          prop="address"
          label="校验数量"
          show-overflow-tooltip>
        </el-table-column>

        <el-table-column
          prop="address"
          label="接收日期"
          show-overflow-tooltip>
        </el-table-column>

        <el-table-column
          prop="address"
          label="接收人员"
          show-overflow-tooltip>
        </el-table-column>

        <el-table-column
          prop="address"
          label="接收数量"
          show-overflow-tooltip>
        </el-table-column>

      </el-table>
    </template>

  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  methods: {
    handleClose(done) {
      this.$confirm('确认关闭？')
        .then(_ => {
          done();
        })
        .catch(_ => {});
    },

    fun1() {
      this.$alert('一个入库单只能判定一次，此入库单已被判定',  {
        confirmButtonText: '确定',
        callback: action => {
          this.$message({
            type: 'info',
            message: `action: ${ action }`
          });
        }
      });
    }
  },
  data(){
    return{
      dialogVisible:false,
      tableData:[{
        status:'合格',
        name:'581',
        address:'叶武',
        submittime:'2020-9-1',
        aps:'dwnp2009',
        dd:'151661',
        wlcode:'sdfae',
        wlname:'QXAS-F305',
        khcode:'KN0049',
        khname:'山东海信',
        jssl:'4079',
        zjzt:'合格',
        bhgyy:''




      },
        {
          customer: '8月25日',
          code: '8月29日',
          type: '珠海凌达',
          amount: '上海海程',
          ProductDate: 'RC440477',
          BoxNumber: 'QX-172C130',
          issuer: '正常机',
          IssueTime: '客户无要求',
          SignPerson:20,
          SignTime:'尾数异常',
          SignStatus:'需打包尾数20台',
          xingneng:'',
          jindu:'未处理',
          bumen:'计划部，总装分厂',
          ren:'黄永锋，张国建',
          yijian:'性能合格',
          zhuan:'质控部'
        },
        {
          customer: '8月25日',
          code: '8月29日',
          type: '珠海凌达',
          amount: '上海海程',
          ProductDate: 'RC440477',
          BoxNumber: 'QX-172C130',
          issuer: '正常机',
          IssueTime: '客户无要求',
          SignPerson:20,
          SignTime:'尾数异常',
          SignStatus:'需打包尾数20台',
          xingneng:'',
          jindu:'未处理',
          bumen:'计划部，总装分厂',
          ren:'黄永锋，张国建',
          yijian:'性能合格',
          zhuan:'质控部'
        }],
      options: [{
        value: '选项1',
        label: '格力'
      }, {
        value: '选项2',
        label: '外销订单'
      }, ],
    }
  }

}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.total{

}
.btn1{
  margin-left: 920px;
}

</style>

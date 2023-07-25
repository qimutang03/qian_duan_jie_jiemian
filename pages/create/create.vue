<template>
	<view>
		<el-form ref="form" :model="form" label-width="80px">
		  <el-form-item label="单号">
		    <el-input  v-model="form.name"></el-input>
		  </el-form-item>
		  
		  <el-form-item label="单据时间">
		    <el-col :span="11">
		      <el-date-picker type="date" placeholder="选择日期" v-model="form.date1" style="width: 100%;"></el-date-picker>
		    </el-col>
		    <el-col class="line" :span="2"> </el-col>
		    <!-- <el-col :span="11">
		      <el-time-picker placeholder="选择时间" v-model="form.date2" style="width: 100%;"></el-time-picker>
		    </el-col> -->
		  </el-form-item>
		  <!-- <el-form-item label="即时配送">
		    <el-switch v-model="form.delivery"></el-switch>
		  </el-form-item> -->
		  <!-- <el-form-item label="活动性质">
		    <el-checkbox-group v-model="form.type">
		      <el-checkbox label="美食/餐厅线上活动" name="type"></el-checkbox>
		      <el-checkbox label="地推活动" name="type"></el-checkbox>
		      <el-checkbox label="线下主题活动" name="type"></el-checkbox>
		      <el-checkbox label="单纯品牌曝光" name="type"></el-checkbox>
		    </el-checkbox-group>
		  </el-form-item> -->
		  <el-form-item label="单据类型">
		    <el-radio-group v-model="form.resource">
		      <el-radio label="入库"></el-radio>
		      <el-radio label="出库"></el-radio>
		    </el-radio-group>
		  </el-form-item>
		  <el-form-item label="送货方式">
		    <el-select v-model="form.region" placeholder="请选择送货方式">
		      <el-option label="自提" value="pick_up"></el-option>
		      <el-option label="送货" value="deliver_goods"></el-option>
		    </el-select>
		  </el-form-item>
		  <el-form-item label="送货地址">
		    <el-input type="textarea" v-model="form.desc"></el-input>
		  </el-form-item>
		  <el-form-item>
		    <el-button type="primary" @click="onSubmit">立即创建</el-button>
		    <el-button>取消</el-button>
		  </el-form-item>
		</el-form>
		<!-- 产品名下 -->
		<el-table
		    :data="tableData"
		    height="250"
		    border
		    style="width: 100%">
		    <el-table-column
		      prop="date"
		      label="日期"
		      width="180">
		    </el-table-column>
		    <el-table-column
		      prop="name"
		      label="姓名"
		      width="180">
		    </el-table-column>
		    <el-table-column
		      prop="address"
		      label="地址">
		    </el-table-column>
		  </el-table>
		
	</view>
	
</template>

<script>
  export default {
    data() {
      return {
        form: {
          name: '',
          region: '',
          date1: '',
          date2: '',
          delivery: false,
          type: [],
          resource: '',
          desc: ''
        },
		tableData: [{
		          date: '2016-05-03',
		          name: '王小虎',
		          address: '上海市普陀区金沙江路 1518 弄'
		        }, {
		          date: '2016-05-02',
		          name: '王小虎',
		          address: '上海市普陀区金沙江路 1518 弄'
		        }, {
		          date: '2016-05-04',
		          name: '王小虎',
		          address: '上海市普陀区金沙江路 1518 弄'
		        }, {
		          date: '2016-05-01',
		          name: '王小虎',
		          address: '上海市普陀区金沙江路 1518 弄'
		        }, {
		          date: '2016-05-08',
		          name: '王小虎',
		          address: '上海市普陀区金沙江路 1518 弄'
		        }, {
		          date: '2016-05-06',
		          name: '王小虎',
		          address: '上海市普陀区金沙江路 1518 弄'
		        }, {
		          date: '2016-05-07',
		          name: '王小虎',
		          address: '上海市普陀区金沙江路 1518 弄'
		        }]
      }
    },
    methods: {
      onSubmit() {
        console.log(this.form.region, this.form.resource);
      }
    }
  }
</script>

<style>

</style>

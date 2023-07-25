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
		    style="width: 100%">
		    <el-table-column type="expand">
		      <template slot-scope="props">
		        <el-form label-position="left" inline class="demo-table-expand">
		          <el-form-item label="商品名称">
		            <span>{{ props.row.name }}</span>
		          </el-form-item>
		          <el-form-item label="所属店铺">
		            <span>{{ props.row.shop }}</span>
		          </el-form-item>
		          <el-form-item label="商品 ID">
		            <span>{{ props.row.id }}</span>
		          </el-form-item>
		          <el-form-item label="店铺 ID">
		            <span>{{ props.row.shopId }}</span>
		          </el-form-item>
		          <el-form-item label="商品分类">
		            <span>{{ props.row.category }}</span>
		          </el-form-item>
		          <el-form-item label="店铺地址">
		            <span>{{ props.row.address }}</span>
		          </el-form-item>
		          <el-form-item label="商品描述">
		            <span>{{ props.row.desc }}</span>
		          </el-form-item>
		        </el-form>
		      </template>
		    </el-table-column>
		    <el-table-column
		      label="商品 ID"
		      prop="id">
		    </el-table-column>
		    <el-table-column
		      label="商品名称"
		      prop="name">
		    </el-table-column>
		    <el-table-column
		      label="描述"
		      prop="desc">
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
		          id: '12987122',
		          name: '好滋好味鸡蛋仔',
		          category: '江浙小吃、小吃零食',
		          desc: '荷兰优质淡奶，奶香浓而不腻',
		          address: '上海市普陀区真北路',
		          shop: '王小虎夫妻店',
		          shopId: '10333'
		        }, {
		          id: '12987123',
		          name: '好滋好味鸡蛋仔',
		          category: '江浙小吃、小吃零食',
		          desc: '荷兰优质淡奶，奶香浓而不腻',
		          address: '上海市普陀区真北路',
		          shop: '王小虎夫妻店',
		          shopId: '10333'
		        }, {
		          id: '12987125',
		          name: '好滋好味鸡蛋仔',
		          category: '江浙小吃、小吃零食',
		          desc: '荷兰优质淡奶，奶香浓而不腻',
		          address: '上海市普陀区真北路',
		          shop: '王小虎夫妻店',
		          shopId: '10333'
		        }, {
		          id: '12987126',
		          name: '好滋好味鸡蛋仔',
		          category: '江浙小吃、小吃零食',
		          desc: '荷兰优质淡奶，奶香浓而不腻',
		          address: '上海市普陀区真北路',
		          shop: '王小虎夫妻店',
		          shopId: '10333'
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
  .demo-table-expand {
    font-size: 0;
  }
  .demo-table-expand label {
    width: 90px;
    color: #99a9bf;
  }
  .demo-table-expand .el-form-item {
    margin-right: 0;
    margin-bottom: 0;
    width: 50%;
  }
  
</style>

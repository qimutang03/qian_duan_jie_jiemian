<template>
	<view class="page">
		<leftBtns></leftBtns>
		<view class="right">
			<view class="head"><text>用户名：张三</text></view>
			<view class="search">
				<el-input placeholder="请输入搜索内容" v-model="input2" class="input-with-select">
					<el-button slot="append" icon="el-icon-search" @click="search"></el-button>
				</el-input>
			</view>
			<view class="buttons">
				<!-- <view class="left">
					<el-button size="medium" type="primary" plain @click="chuanjian">创建</el-button>
					<el-button size="medium" type="info" plain @click="daoru">导入</el-button>
				</view> -->
				<view class="center">
					<el-dropdown size="medium" split-button type="primary">
						筛选
						<el-dropdown-menu slot="dropdown">
							<el-dropdown-item>黄金糕</el-dropdown-item>
							<el-dropdown-item>狮子头</el-dropdown-item>
							<el-dropdown-item>螺蛳粉</el-dropdown-item>
							<el-dropdown-item>双皮奶</el-dropdown-item>
							<el-dropdown-item>蚵仔煎</el-dropdown-item>
						</el-dropdown-menu>
					</el-dropdown>
					<el-dropdown size="medium" split-button type="primary" style="margin: 0 10px;">
						分组
						<el-dropdown-menu slot="dropdown">
							<el-dropdown-item>黄金糕</el-dropdown-item>
							<el-dropdown-item>狮子头</el-dropdown-item>
							<el-dropdown-item>螺蛳粉</el-dropdown-item>
							<el-dropdown-item>双皮奶</el-dropdown-item>
							<el-dropdown-item>蚵仔煎</el-dropdown-item>
						</el-dropdown-menu>
					</el-dropdown>
					<el-dropdown size="medium" split-button type="primary" icon="el-icon-search" @command="handleCommand">
						收藏
						<el-dropdown-menu slot="dropdown">
							<el-dropdown-item command="a">黄金糕</el-dropdown-item>
							<el-dropdown-item command="b">狮子头</el-dropdown-item>
							<el-dropdown-item command="c">螺蛳粉</el-dropdown-item>
							<el-dropdown-item command="d">双皮奶</el-dropdown-item>
							<el-dropdown-item command="e">蚵仔煎</el-dropdown-item>
						</el-dropdown-menu>
					</el-dropdown>
				</view>
			</view>
			<view class="table">
				<el-table stripe="stripe" ref="multipleTable" :data="tableData" tooltip-effect="dark" style="width: 100%"
					@selection-change="handleSelectionChange">
					<el-table-column prop="index" label="#" width="40">
					</el-table-column>
					<el-table-column type="selection" width="55">
					</el-table-column>
					<el-table-column prop="name" label="product Name" width="150">
					</el-table-column>
					<!-- <el-table-column prop="company_id" label="compary" width="120">
					</el-table-column> -->
					<<!-- el-table-column prop="client" label="Client" show-overflow-tooltip>
						</el-table-column> -->
						<!-- <el-table-column prop="cardBoard" label="card board" show-overflow-tooltip>
					</el-table-column> -->
						<el-table-column prop="box_code" label="Box Code" show-overflow-tooltip>
						</el-table-column>
						<el-table-column prop="quantity_boxes" label="Number Boxse" show-overflow-tooltip>
						</el-table-column>
						<el-table-column prop="quantity" label="Quantity" show-overflow-tooltip>
						</el-table-column>
				</el-table>
				<el-pagination background @size-change="handleSizeChange" @current-change='sizeChange' @prev-click="prevClick"
					@next-click="nextClick" layout="prev, pager, next" :total="1000">
				</el-pagination>
			</view>
			<button @click="goPage">跳转页面，测试使用</button>
			<button @click="goPageLogin">跳转登录页面，测试使用</button>
		</view>
	</view>
</template>

<script>
	import axios from 'axios'
	import VueAxios from 'vue-axios'
	import leftBtns from '../../components/leftBtns.vue'
	export default {
		components: {
			leftBtns
		},
		data() {
			return {
				stripe: true,
				input2: '', //搜索框内容
				tableData: [],
				multipleSelection: [] //多选选中的数据
			}
		},
		onLoad() {
			this.GetDataInStock()
		},
		methods: {

			GetDataInStock() {
				axios.get('http://127.0.0.1:8060/zh_CN/accurate/inventory/' + 22677, {
						// params: {
						// 	id: 22677
						// }
					}).then(res => {
						this.tableData = res.data
						console.log(this.tableData)
					})
					.catch(res => {
						// console.log(res.data)
					})
			},



			// chuanjian() {
			// 	console.log('点击创建');
			// },
			// daoru() {
			// 	console.log('点击导入');
			// },
			search() {
				console.log('点击搜索，输入内容为：', this.input2);
			},
			handleSelectionChange(val) {
				this.multipleSelection = val;
			},
			handleCommand(command) {
				console.log('command', command);
			},
			handleSizeChange(size) { //pageSize 改变时会触发
				console.log(size, 'size');
			},
			sizeChange(currentPage) { //currentPage 改变时会触发
				console.log(currentPage)
			},
			prevClick(currentPage) { //用户点击上一页按钮改变当前页后触发
				console.log(currentPage)
			},
			nextClick(currentPage) { //用户点击下一页按钮改变当前页后触发
				console.log(currentPage)
			},
			goPage() {
				uni.navigateTo({
					url: '/pages/index1/index1'
				})
			},
			goPageLogin() {
				uni.navigateTo({
					url: '/pages/login/login'
				})
			}
		}
	}
</script>

<style>
	.page {
		display: flex;
	}
	,.right {
		flex: 1;
	}
	.head {
		width: 100%;
		background-color: #faebd7;
		height: 40px;
		line-height: 40px;
		/* text-align: right; */
		padding-left: 15px !important;
	}
	
	.buttons {
		margin: 5px 0;
		padding: 0 5px;
		display: flex;
		justify-content: space-between;
	}
	
	.el-pagination {
		text-align: center;
	}
</style>